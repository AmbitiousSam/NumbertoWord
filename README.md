# NumbertoWord

<!DOCTYPE html>
<html lang="en">
<script>
	function isNumberKey(evt)
	{
    var charCode = (evt.which) ? evt.which : evt.keyCode
    if (charCode > 31 && (charCode < 48 || charCode > 57))
        return false;
    return true;
	}
window.onload=function(){
var btn=document.getElementById("btn");
btn.onclick=function()
	{
		var num=document.getElementById("number").value;
		var res=document.getElementById("result");
		if(isNaN(num))
		{
			res.value="not a number"
		}
		else if(num<0 || num>999)
		{
 		res.value="out of range"
		}
		else
		{
		res.value=convert(num);	
		}
		return false;
	}

}
//actual conversion
var ones=['','one','two','three','four','five','six','seven','eight','nine'];
var tens=['','','twenty','thirty','fourty','fifty','sixty','seventy','eighty','ninety'];
var teens=['ten','eleven','twelve','thirteen','fourteen','fifteen','sixteen','seventeen','eighteen','nineteen'];

function convert_hundreds(num)
	{
		if(num>99)
		{
			return ones[Math.floor(num/100)]+" hundred "+convert_tens(num%100);
		}
		else
		{
			return  convert_tens(num);
		}
	}
function convert_tens(num)
	{
		if(num<10) return ones[num];
		else if(num>=10 && num<20) return teens[num-10];
		else
		{
			return tens[Math.floor(num/10)]+""+ones[num%10];
		}
	}
function convert(num)
	{
		if(num==0) return "Zero";
		else return convert_hundreds(num);
	}
</script>
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
</head>
<style>
	#number,#result{align: center;width: 300px;height: 14px;font-size: 12px;margin: 10px;padding: 5px;}
	#btn{align-self: center;width: 100px;height: 20px;background-color: #bebadb;background-blend-mode: lighten;padding: 2px;border-radius: 20px;margin: 5px;}
	#btn:hover{background-color: #000000;color: #00FFFF;}
</style>
<body bgcolor="#c5c4cf">
	<fieldset align ="center">
		<legend>Number to Word Conversion</legend>
		<form>
			Enter Number to be converted :<input type="number" id="number" onkeypress="return isNumberKey(event)" required="true"><br>
			  <input type="submit" style="width: 100px; height: 30px;" id="btn" value="Go!"><br>
			Converted Number is :<input type="text" id="result">
		</form>
	</fieldset>
</body>
</html>
