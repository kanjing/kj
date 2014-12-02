<html>
<head>
	<title>php实现简单的计算功能</title>
</head>
<?php

           $num1=true;
           $num2=true;
           $numa=true;
           $numb=true;
           $message="";
       if (isset($_GET["sub"])){
           if ($_GET["num1"]=="") {
      	     $num1=false;
      	     $message="第一个数不能为空";
              }
           if (!is_numeric($_GET["num1"])) {
           	 $num1=false;
           	 $message="第一个数不是数字";
           }
           if ($_GET["num2"]=="") {
               $num2=false;
      	       $message="第二个数不能为空";
              }
           if (!is_numeric($_GET["num2"])) {
           	   $num2=false;
           	   $message="第二个数不是数字";
           }
        	$sum=0;
     	    switch($_GET["ysf"]) {
     		     case "+":
     			     $sum=$_GET["num1"]+$_GET["num2"];
     			     break;

     			     case "-":
     			     $sum=$_GET["num1"]-$_GET["num2"];
     			     break;

     			     case "*":
     			     $sum=$_GET["num1"]*$_GET["num2"];
     			     break;

     			     case "/":
     		    	$sum=$_GET["num1"]/$_GET["num2"];
     		    	break;

     		    	case "%":
     		    	$sum=$_GET["num1"]%$_GET["num2"];
     		    	break;
     	}
     }

?>
<body>
     <table border="1" align="center" width="400">
            <caption><h1>计算器</h1></caption>
     	    <form action="jsq.php">
     	    	<tr>
     	    		<td>
     	    			<input type="test" size="5" name="num1">
                    </td>
                    <td>
                    	<select name="ysf">
                    		<option value="+" <?php if ($_GET["ysf"]=="+") {echo "selected";} ?> >+</option>
                    		<option value="-"<?php if ($_GET["ysf"]=="-") {echo "selected";} ?>>-</option>
                    		<option value="*"<?php if ($_GET["ysf"]=="*") {echo "selected";} ?>>*</option>
                    		<option value="/"<?php if ($_GET["ysf"]=="/") {echo "selected";} ?>>/</option>
                    		<option value="%"<?php if ($_GET["ysf"]=="%") {echo "selected";} ?>>%</option>

                    	</select>

                    </td>
                    <td>
                    	<input type="test" size="5" name="num2">

                    </td>
                    <td>
                    	<input type="submit" name="sub" value="计算">
                    </td>
                </tr>
                <?php
                    if (isset($_GET["sub"])) {
                    	echo "<tr><td>";
                    	if ($num1&&$num2) {
                    		echo "结果：" .$_GET["num1"]. " " .$_GET["ysf"]. " " .$_GET["num2"]. "=" .$sum;
                    	}else{
                    		echo "$message";
                    	}
                    	echo "</td></tr>";
                    }


                ?>
             </form>
     </table>
</body>
</html>
