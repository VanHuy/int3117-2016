# KTPM2016
# Doãn Văn Huy; Mã Sv: 12020169
# /* JUnit Test */
Bài tập 2 môn kiểm thử phần mềm 2016
* Chương trình mô tả thuật toán QuickSort
 Hàm cần kiểm thử:
    ```javascript
    public void sort(int[] values) {
	    // check for empty or null array
	    if (values ==null || values.length==0){
	      return;
	    }
	    this.numbers = values;
	    number = values.length;
	    quicksort(0, number - 1);
	  }
    ```
* Đo mức độ bao phủ:
 ![Flowchart](https://github.com/truonganhhoang/int3117-2016/blob/master/Nhom-07/DoanVanHuy/BT2/coveaverageBT2.PNG)
* Kết quả test: Đã pass cả 6 testcase

