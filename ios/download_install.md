# IOS APP 下載＆安裝

1. 需修改manifest.plist檔名，與ipa檔名一至

EX:

```
Demo.plist
Demo.ipa
```

2. *.plist放於`https`路徑下，*.ipa則不用

3. 安裝下載url格式為：`itms-services://?action=download-manifest&url=<plist's url>`

EX:

```
itms-services://?action=download-manifest&url=https://localhost/Demo.plist
```

4. 如果將plist放於 AWS S3上則需要新增以下標籤

| key        | value|
| ---------- | -------- |
| MIME types | text/xml |

5. manifest.plist檔案內容如下，也可以透過ＸCode在build APP時自動產生。

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>items</key>
	<array>
		<dict>
			<key>assets</key>
			<array>
				<dict>
					<key>kind</key>
					<string>software-package</string>
					<key>url</key>
					<string>[your ipa file url]</string></string>
				</dict>
				<dict>
					<key>kind</key>
					<string>display-image</string>
					<key>url</key>
					<string>[your appd isplay-image url]</string>
				</dict>
				<dict>
					<key>kind</key>
					<string>full-size-image</string>
					<key>url</key>
					<string>[your full-size-image url]</string>
				</dict>
			</array>
			<key>metadata</key>
			<dict>
				<key>bundle-identifier</key>
				<string>app bundle identifier id</string>
				<key>bundle-version</key>
				<string>1.0</string>
				<key>kind</key>
				<string>software</string>
				<key>title</key>
				<string>test</string>
			</dict>
		</dict>
	</array>
</dict>
</plist>
```

> `software-package`、`full-size-image`、`display-image`與`bundle-identifier`四個參數值依造個人情況進行設置

> `full-size-image`圖片size為512x512

> `display-image`圖片size為52x52
