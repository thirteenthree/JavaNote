### 15.2 FileInputStream读取例子

* FileInputStream()构造方法中可以传一个路径;
* int read()方法,返回值为读取的byte码,-1表示读完
* int read(byte[] buffer)方法,传入一个缓冲字节数组,每次读buffer大小,返回值为读取字节大小(因为最后一次读不能保证读满buffer),-1表示读完;
* vavailable():剩余未读取字节数;
* skip(int n);跳过n个字节;
```Java
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
public class My{
	public static void main(String args[]){
	FileInputStream file=null;
	try{
		file=new FileInputStream("./test");
		byte[] buffer=new byte[4];
		while(true){
			int dataLength = file.read(buffer);
			if (dataLength==-1){
				break;
			}
			System.out.print(new String(buffer,0,dataLength));
		}

	}catch(FileNotFoundException e){
		e.printStackTrace();
	}catch(IOException e){
		e.printStackTrace();
	}finally{
		if(file != null){
			try{
				file.close();
			}catch(IOException e){
				e.printStackTrace();
			}
		}
	}

	}
}

```

