# GridWorld1  
## 阶段一 Vi,Java,Ant和Junit的自学报告  

### Vi:
* 很快就遇上了第一个小错误，文件名有空格，如下面的，只会创建一个叫hello的文件，Vi很明显文件名不要空格  
  <img src="http://imglf6.nosdn.127.net/img/Z281REhERnhNZlhmNHB3cnQ2ZEtHRllvYTRoVmphUzFaTHlZUzVZYnBlR1VNU2FzVStmZ3dBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />    
* 然后开始利用诸如  i  x  来增加删减其中的信息  
  <img src="http://imglf4.nosdn.127.net/img/Z281REhERnhNZlhmNHB3cnQ2ZEtHSFJVOU8xR3VGekI1NW5jNFVDVmN1M3ZMdmdsSThiWTVnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0" /> 
* 例如，输入is，实际上是增加了s一个字母在光标处，而且移动光标的时候时刻记得按Esc键，要退出insert mode大的话按下“:”冒号    
  <img src="http://imglf3.nosdn.127.net/img/Z281REhERnhNZlhmNHB3cnQ2ZEtHTWRuWC9GaU0wWFhZeXVnTURlZjR1QnZNT0xUcllCNU1nPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0" />    
   
* 又例如，输入:set nu，列出每行行号  
   <img src="http://imglf3.nosdn.127.net/img/Z281REhERnhNZlhmNHB3cnQ2ZEtHQ0hUQVlCRzBSRmNXTG5GWTR1Tm1qRkZyNUtDNjRZMFNnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />  
> * Vi总结： 
>   * 用 vi 打开文件后，是处于「命令行模式（command mode）」，您要切换到「插入模式（Insertmode）」才能够输入文字。  
>   * 切换方法：在「命令行模式（command mode）」下按一下字母「i」就可以进入「插入模式（Insert mode）」，这时候你就可以开始输入文字了。  
>   * 编辑好后，需从插入模式切换为命令行模式才能对文件进行保存，切换方法：按「ESC」键。  
>   * 保存并退出文件：在命令模式下输入:wq 即可！ 

### Ant  
* 先创建名字为build.xml的文件
```  
<?xml version="1.0"?>  
<project name="HelloWorld" default="test" basedir="">  
    <target name="test-compile">  
        <javac srcdir="src" destdir="classes/" />  
    </target>  
     <target name="test-run-java">  
        <java classname="helloworld">  
            <classpath>  
                <pathelement path="classes" />  
            </classpath>  
        </java>  
    </target>  
</project>  
```  

* 将helloworld.java放进文件夹src,同时mkdir classes  

``` 
ant test-compile//编译，相当于javac
ant test-run-java//运行

```  

 * 运行结果如下： 
<img src="http://imglf3.nosdn.127.net/img/Z281REhERnhNZldLRkNMQzBuTHR4RkhVQUt4Y0VTMm95endrWkRVR2hpSWFmNXhPbVdYY1ZRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />


  
