# Java使用QRCode.jar生成与解析二维码 （2019-04-16）

这个是我根据好几个人的代码修改而成的生成并解读二维码的java程序   
主要由3个文件组成：   
   
**1.control.java**   
**2.MyQRCodeImage.java**   
**3.QRCode.jar**   
   
主要思路就是main函数控制encode类和decode类   
class encode生成并存储二维码图片   
class decode解码图片并输出二维码图片信息   
MyQRCodeImage.java是读取图片接口   
QRCode.jar是二维码相关运算的依赖包   
   
去下面给出的地址下载QRCode.jar包，此jar包已经包括 生成与解析 。官网下载到的jar包是没有解析的。
[**https://files.cnblogs.com/files/bigroc/QRCode.zip**](https://files.cnblogs.com/files/bigroc/QRCode.zip "下载QRCode")

特别感谢 [bigroc](https://www.cnblogs.com/bigroc/) 的文章[《Java使用QRCode.jar生成与解析二维码》](http://www.cnblogs.com/bigroc/p/7496995.html)   

代码如下：

**control.java**
```java
//control.java
package com.allenem.qrcode;

import com.swetake.util.Qrcode;
import jp.sourceforge.qrcode.QRCodeDecoder;

import javax.imageio.ImageIO;
import java.awt.*;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;
import java.util.Random;

public class control {
    public static void main(String[] args) {
    	String data="https://github.com/Allenem";
    	long t = System.currentTimeMillis();
    	Random rand = new Random(t);
    	int [][] r = new int[37][37];
    	for(int i=0; i<37; i++) {
    		for(int j=0; j<37; j++) {
    			r[j][i] = rand.nextInt(2);
    		}
    	}
    	// 生成二维码
    	control.encode(data, "qrcodeimage/qrcode.jpg");

    	// 解析二维码
    	control.decode("qrcodeimage/qrcode.jpg");
    }
    
    //生成并输出二维码
    private static boolean encode(String srcValue, String qrcodePicfilePath){
    	int MAX_DATA_LENGTH = 200;
    	byte[] d = srcValue.getBytes();
    	int dataLength = d.length;
    	int imageWidth = 189;
    	int imageHeight = imageWidth;
    	BufferedImage bi = new BufferedImage(imageWidth, imageHeight,BufferedImage.TYPE_INT_RGB);//缓冲区
    	Graphics2D g = bi.createGraphics();//绘图
    	g.setBackground(Color.WHITE);
    	g.clearRect(0, 0, imageWidth, imageHeight);
    	g.setColor(Color.BLACK);
    	if (dataLength > 0 && dataLength <= MAX_DATA_LENGTH) {
    		Qrcode qrcode = new Qrcode();
    		/**
    		 * correction level分为
    		 * level L : 最大 7% 的错误能够被纠正；
    		 * level M : 最大 15% 的错误能够被纠正；
             * level Q : 最大 25% 的错误能够被纠正；
             * level H : 最大 30% 的错误能够被纠正；
             */
    		qrcode.setQrcodeErrorCorrect('Q');
    		qrcode.setQrcodeEncodeMode('B');//注意版本信息 N代表数字 、A代表 a-z,A-Z、B代表其他
    		qrcode.setQrcodeVersion(5);//版本号  1-40
    		boolean[][] b = qrcode.calQrcode(d);//让字符串生成二维码
    		int qrcodeDataLen = b.length;
    		for (int i = 0; i < qrcodeDataLen; i++) {
    			for (int j = 0; j < qrcodeDataLen; j++) {
    				if (b[j][i]) {
    					g.fillRect(j * 5 + 2, i * 5 + 2, 5, 5);//2为偏移量，5,5为矩形小块宽高
    					}
    			}
    		}
    	System.out.println("二维码成功生成！！");
    	} else {
    		System.out.println( dataLength +"大于"+ MAX_DATA_LENGTH);
    		return false;
    	}
    	g.dispose();
    	bi.flush();
    	File f = new File(qrcodePicfilePath);
    	String suffix = f.getName().substring(f.getName().indexOf(".")+1, f.getName().length());
    	System.out.println("二维码输出成功！！");
    	try {
    		ImageIO.write(bi, suffix, f);
    		} catch (IOException ioe) {
    			System.out.println("二维码生成失败" + ioe.getMessage());
    		}
    	return true;
    }
    
    //解析二维码
    private static String decode(String qrcodePicfilePath) {
    	System.out.println("开始解析二维码！！");
    	
    	//读取二维码图像数据
    	File imageFile = new File(qrcodePicfilePath);
    	BufferedImage image = null;
    	try {
    		image = ImageIO.read(imageFile);
    	} catch (IOException e) {
    		System.out.println("读取二维码图片失败： " + e.getMessage());
    		return null;
    	}
    	
		//解二维码
    	QRCodeDecoder decoder = new QRCodeDecoder();
    	String decodedData = new String(decoder.decode(new MyQRCodeImage(image))); //MyQRCodeImage要有接口文件
    	System.out.println("解析内容如下："+decodedData);
    	return decodedData;
    }
}
```

**MyQRCodeImage.java** 
```java
//MyQRCodeImage.java
package com.allenem.qrcode;

import jp.sourceforge.qrcode.data.QRCodeImage;
import java.awt.image.BufferedImage;
/**
 * 实现QRCodeImage接口，
 * 设置解码的图片信息
 * 告诉codeDecoder.decode()将要解析的图片类型
 */

public class MyQRCodeImage implements QRCodeImage{
	
    BufferedImage bufferedImage;
    
    public MyQRCodeImage(BufferedImage bufferedImage){
        this.bufferedImage=bufferedImage;
    }

    //宽
    @Override
    public int getWidth() {
        return bufferedImage.getWidth();
    }

    //高
    @Override
    public int getHeight() {
        return bufferedImage.getHeight();
    }

    //像素还是颜色
    @Override
    public int getPixel(int i, int j) {
        return bufferedImage.getRGB(i,j);
    }
}
```
   
文件框架如下：

![文件框架.png](https://upload-images.jianshu.io/upload_images/7728717-78a61087542051ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

效果图如下：  

![运行代码截图.png](https://upload-images.jianshu.io/upload_images/7728717-efbdd8a0da01b960.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

生成二维码图片如下：

 ![qrcode.jpg](https://upload-images.jianshu.io/upload_images/7728717-187c433d121096de.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)