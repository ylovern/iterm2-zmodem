在 macOS 下，iterm2 实现与服务器进行文件上传和下载功能。
1. install lrzsz
```
brew install lrzsz
```
2. download iterm2-recv-zmodem.sh iterm2-send-zmodem.sh to /usr/local/bin
```
cd /usr/local/bin
wget https://raw.githubusercontent.com/Jiwei0/iterm2-zmodem/master/iterm2-recv-zmodem.sh 
wget https://raw.githubusercontent.com/Jiwei0/iterm2-zmodem/master/iterm2-send-zmodem.sh
```
3. grant shell scripts exec permission
```
chmod +x  iterm2-recv-zmodem.sh iterm2-send-zmodem.sh
```
4. 在 iterm2 profiles -> default -> editProfiles -> Advanced 中添加 Tirgger
添加两条trigger，分别设置 Regular expression，Action，Parameters，Instant 如下：

	- 第一条配置

   		Regular expression: rz waiting to receive.\*\*B0100 
	 		
   		Action: Run Silent Coprocess
	 		
   		Parameters: /usr/local/bin/iterm2-send-zmodem.sh
	 		
   		Instant: checked
   
	- 第二条配置
	
   		Regular expression: \*\*B00000000000000
	 		
   		Action: Run Silent Coprocess
	 		
   		Parameters: /usr/local/bin/iterm2-recv-zmodem.sh
	 		
   		Instant: checked


