### Credit card validation

LUHN算法，主要用来计算信用卡等证件号码的合法性。
1、从卡号最后一位数字开始,偶数位乘以2,如果乘以2的结果是两位数，将两个位上数字相加保存。
2、把所有数字相加,得到总和。
3、如果信用卡号码是合法的，总和可以被10整除。
/**
* 验证是否为银行卡号 使用luhn 方法验证

  ~~~java
  public static boolean isBankNumber(String bankNumber) {
    try{
      int[] cardNumArr = new int[bankNumber.length()];
      for(int i =0;i<bankNumber.length();i++){
        cardNumArr[i] = Integer.valueOf(String.valueOf(bankNumber.charAt(i)));
      }
      for(int i= bankNumber.length()-2;i>=0;i-=2){
        //位运算乘2
        cardNumArr[i] <<=1;
        cardNumArr[i] = cardNumArr[i]/10+cardNumArr[i]%10;
      }
      int sum =0;
      for(int i =0;i<bankNumber.length();i++){
        sum+=cardNumArr[i];
      }
      return sum % 10 == 0;
      
    }
    catch(Exception e){
      return false;
    }
    
  }
  ~~~

  

