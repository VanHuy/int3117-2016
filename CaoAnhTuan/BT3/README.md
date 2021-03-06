#Bài tập tuần 7

##Mô tả bài toán
* Kiểm tra số được nhập có phải số điện thoại hay không
* Các điều kiện:
	* Kí tự đầu tiên phải là số ‘0’.
	* Độ dài chuỗi kí tự phải là 10 hoặc 11.
	* Kí tự trong chuỗi phải là một số.

##Lớp cần kiểm thử
```java
	public class SoDienThoai {
		int i=1;
		public static String s1 = "La mot so dien thoai hop le";
    		public static String s2 = "Khong phai la mot so dien thoai hop le";

    		public String ktraSDT(String s3) {
    			boolean dk1 = (s3.charAt(0)=='0');
        		boolean dk2 = (s3.length()==10 || s3.length()==11);

        		if (dk1 && dk2){
            			while (i < s3.length()) {
                			if (s3.charAt(i)>=48 && s3.charAt(i)<=57){
                				i++;
                			}else {
                    				break;
                			}
                
            			}
        		}
        		if (i == s3.length()) {
            			return s1;
        		}else{
        			return s2;
        		}
    		}
	}
```

##Đồ thị chu trình
![flow](https://github.com/ducanhk58uet/int3117-2016/blob/master/CaoAnhTuan/BT3/img/DoThiChuTrinh.jpg?raw=true)

##Xác định du-pair cho từng biến
* Biến DieuKien1:

du-pair|path(s)
-------|-------|
2-4|2-3-4

* Biến DieuKien2:

du-pair|path(s)
-------|-------|
3-4|3-4

* Biến i:

du-pair|path(s)
-------|-------|
1-8|1-2-3-4-5-6-8
1-8|1-2-3-4-5-6-7-5-8
1-8|1-2-3-4-8
7-8|7-5-8
7-8|7-5-6-8

##Sinh test cases cho các biến

\#	|Tên biến|path(s)|Input Value of String s |Output |Expected |Result
----|--------|--------|-----------------------|-------|---------|------|
0.	|DieuKien1|2-3-4 |0906130$895				  |Error  |Error	|pass
1.	|DieuKien2|3-4   |9061308956				  |Error  |Error	|pass	
2.	|i        |1-2-3-4-5-6-8         |090613089v			  |Error  |Error	|pass
3.	|         |1-2-3-4-5-6-7-5-8 |0906130895			  |Ok    	  |Ok   		|pass
4.	|         |1-2-3-4-8   |09061v30%89				  |Error	  |Error		|pass

##Unit Test cho các ca kiểm thử
```java
        @Test
	public void test0() {
		SoDienThoai soDienThoai = new SoDienThoai();
		Assert.assertEquals(soDienThoai.ktraSDT("0906130$895"), soDienThoai.s2);
	}

	@Test
	public void test1() {
		SoDienThoai soDienThoai = new SoDienThoai();
		Assert.assertEquals(soDienThoai.ktraSDT("9061308956"), soDienThoai.s2);
	}
	
	@Test
	public void test2() {
		SoDienThoai soDienThoai = new SoDienThoai();
		Assert.assertEquals(soDienThoai.ktraSDT("090613089v"), soDienThoai.s2);
	}
	
	@Test
	public void test3() {
		SoDienThoai soDienThoai = new SoDienThoai();
		Assert.assertEquals(soDienThoai.ktraSDT("0906130895"), soDienThoai.s2);
	}
	
	@Test
	public void test4() {
		SoDienThoai soDienThoai = new SoDienThoai();
		Assert.assertEquals(soDienThoai.ktraSDT("09061v30%89"), soDienThoai.s2);
	}
```
##Đo mức độ bao phủ:
![](https://github.com/ducanhk58uet/int3117-2016/blob/master/CaoAnhTuan/BT3/img/Cov_TestAllDuPath.jpg?raw=true)

##Nhận xét
* Chung:
	* Cả 2 đều hỗ trợ quá trình tạo test cases khá thuận lợi
	* Độ bao phủ của cả 2 đều tương tự nhau
	* Cả 2 đều chưa quét qua trường hợp boolean
* Ưu thế của MCDC:
	* Dùng MCDC sẽ kiểm soát được các câu lệnh điệu kiện tốt hơn
	* Quá trình sinh test cases sẽ quét hết trường hợp
* Ưu thế của All-du-Path:
	* Sinh test cases theo luồng đồ thị nên rành mạch và dễ dàng hơn
	* Có thể phủ qua một số trường hợp câu lệnh điều kiện trên đường đi qua của thị