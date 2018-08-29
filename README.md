# QrcodeProject
##功能描述
web端的二维码生成和下载功能
##使用的插件
- jquery
- qrcode

##生成二维码
	var qrcode = new QRCode(document.getElementById("qrcode"), {
        width : 200,
        height : 200
    });
    var text = '1234567789';
    qrcode.makeCode(text);
##二维码的下载
	<a id="downloadLink"></a>
	/**imageName,生成二维码的名字
	**/
	function downloadClick (imageName) {
        // 获取base64的图片节点
        var img = $('#qrcode img')[0];
        // 构建画布
        var canvas = document.createElement('canvas');
        canvas.width = img.width;
        canvas.height = img.height;
        canvas.getContext('2d').drawImage(img, 0, 0);
        // 构造url
        url = canvas.toDataURL('image/png');
        // 构造a标签并模拟点击
        var downloadLink = $('#downloadLink').attr("href", url).attr("download", imageName+".png");
        downloadLink[0].click();
    }
