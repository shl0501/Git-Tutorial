## 미션1
* 요구사항 역분석하기
  * 지역 판단 조건
    * 전달받은 전화번호의 두번재 문자(telno[1])가
      * '2'라면 서울로 판단
      * 그 외의 경우 처음 3개의 숫자를 잘라서 문자열로 만든 후, 해당 문자열을 map안의 문자열과 비교하여 지역 판단
  * 휴대폰 번호판단 조건
    * telno[1]이 1이라면 휴대폰 번호로 판단
    * 전화번호 길이가 11이라면 "O"
    * '010'이라면 "O"
    * 그 외는 "X"
* 개선하기
  * '-'문자가 포함되어 있는 경우 해당 문자를 제거한다. 이를 위해서 split('-')이라는 문법을 사용하여 '-' 문자 단위로 문자열을 구분하였고, 이후 join('')을 통해 나눠진 문자열들을 하나의 문자열로 합쳤다.

        let tel = telno.split('-').join('');

  해당 코드가 잘 작동하는지 확인하기 위해 '-'문자가 제거된 번호를 출력하여 정상적으로 코드가 동작하는지를 확인하였다.
  
        let tel = telno;
        if(telno.length > 12)
        {
            tel = telno.split('-').join('');    //개선하기 => '-' 문자가 있을 경우 제거하여 동작하도록 코드수정
            console.log("기존번호 : " + telno + "\n" + "변경된 번호 : " + tel);
        }
  
* 새로운 요구사항 추가
  * 002, 001이 있는 경우
    * tel[1] === '0'일 경우, top === "001" || top === "002"라면 국제전화로 판단하고, substring(3) 문법을 통해 해당 문자열을 제거하였다.

          let new_tel = tel.substring(3); //001, 002 제거

    이후 만약 new_tel.length >12 || new_tel.length <8 일 경우 "X"를 그 이외의 경우 "O"를 return 하였다.

    해당 코드가 정상적으로 동작하는지 확인하기 위해 다음의 코드를 추가하여 결과를 확인한다.

        console.log(solution("002-1234-1234")); //return ['국제전화', 'O']
        console.log(solution("002-1234-1234-1212-1234")); //return ['국제전화', 'X']

    
