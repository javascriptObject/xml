# xml

pet1.xml
fdfsdfds
```
<?xml version="1.0" encoding="UTF-8"?>
<宠物们>
	<狗狗 id="1">		
		<姓名>YAYA</姓名>
		<健康值>100</健康值>
		<亲密度>0</亲密度>
		<品种>酷酷的雪娜瑞</品种>
	</狗狗>
	<狗狗 id="2">		
		<姓名>OUOU</姓名>
		<健康值>90</健康值>
		<亲密度>15</亲密度>
		<品种>聪明的拉布拉多犬</品种>
	</狗狗>
</宠物们>
```

student.css

```
student{
	display: block;
	font-size:24px;
}
name,age,school{
	background-color:red;
	color:white;
}
```

student.dtd

```
<!ELEMENT students (student*)>
<!ELEMENT student (name,age,school)>
<!ELEMENT name (#PCDATA)>
<!ELEMENT age (#PCDATA)>
<!ELEMENT school (#PCDATA)>
```

student.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE students SYSTEM "student.dtd">
<?xml-stylesheet type="text/css" href="student.css"?>
<students>
	<student>
		<name>小明</name>
		<age>10</age>
		<school>北大附小</school>
	</student>
	<student>
		<name>小红</name>
		<age>15</age>
		<school>清华中学</school>
	</student>
	<student>
		<name>小强</name>
		<age>99</age>
		<school>小强小学</school>
	</student>
	<student>
		<name>小灰灰</name>
		<age>12</age>
		<school>学校</school>
	</student>
</students>
```

xml.html

```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title></title>
    <script>
        function getval(){
            var xmlhttp = new XMLHttpRequest();
            xmlhttp.open("GET","student.xml",false);
            xmlhttp.send(null);
            var xmlText = xmlhttp.responseXML;

//            if (window.DOMParser)
//            {
//                parser=new DOMParser();
//                xmlDoc=parser.parseFromString(xmlText,"text/xml");
//            }
//            else // Internet Explorer
//            {
//                xmlDoc=new ActiveXObject("Microsoft.XMLDOM");
//                xmlDoc.async="false";
//                xmlDoc.load("student.xml");
//            }

            for(var i = 0; i < xmlText.getElementsByTagName("name").length; i++){
                document.getElementById("student").innerHTML += "姓名："+xmlText.getElementsByTagName("name")[i].childNodes[0].nodeValue+"<br/>";
                document.getElementById("student").innerHTML += "年龄："+xmlText.getElementsByTagName("age")[i].childNodes[0].nodeValue+"<br/>";
                document.getElementById("student").innerHTML += "学校："+xmlText.getElementsByTagName("school")[i].childNodes[0].nodeValue+"<br/>";
                document.getElementById("student").innerHTML += "<br/>";
            }
        }
    </script>
</head>
<body>
    <input type="button" value="提取
