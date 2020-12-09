# js_10_20201209
javascript 생성자함수 예제


    <!-- 
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    js_22.html
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        => 객체의 전신인 [생성자 함수]를 공부해보자.
        => 자바스크립트에서는 사용자 정의 [생성자 함수]를 만들고 [생성자 함수]를 객체화 할 수 있다.
          (사용자 정의 : '개발자가 직접 만든' 이라는 뜻)
        => [생성자 함수]는 일반 함수와 구조가 다르다.
        => [생성자 함수]의 이름은 <관용적으로 대문자> 로 시작한다.
        => [생성자 함수]의 내부에는 **<속성변수>**와 **<메소드>**가 존재한다.
        => 개발자가 만든 [생성자 함수]로 만들어진 객체를 [사용자 정의 객체]라고 부르기도 한다.
        => <참고>[생성자 함수]는 주로 솔루션 회사에서 많이 사용된다.
        => <참고>[생성자 함수는 SI쪽에서는 많이 사용되지 않는다..
        ---------------------------------------------
        호출하기 위한게 아니라 **객체화**(객체를 생성) 하기 위한 함수 => [생성자 함수]
        ---------------------------------------------
        [생성자 함수] 형태
        ---------------------------------------------
        function 생성자함수명(매개변수){

             this.속성변수명 = 데이터;

             var 지역변수명 = 데이터; (this.이 없으면 지역변수다.)

             this.메소드명 = function([매개변수명]){
                  실행구문;
             }
        }
        ---------------------------------------------
          속성변수는 0개 이상 선언 가능.
          메소드는 0개 이상 선언 가능.
          실무적으로는 속성변수 또는 메소드가 1개 이상 선언되야한다.
          지역변수는 0개 이상 선언 가능.
          지역변수는 속성변수 또는 메소드에서만 호출이 가능하다.
          즉 개체 생성 후 지역변수를 호출할 수는 없다.
          -----------------------------------------
          생성자 함수의 객체화 형식 => var 객체참조변수명 = new 생성자명([데이터]);
          객체의 속성변수 호출 형식 => 객체참조변수명.속성변수명
          객체의 메소드 호출 형식	=> 객체참조변수명.메소드명([데이터])
        ---------------------------------------------
     -->
    <!DOCTYPE html>
    <html>
    <head><meta charset="utf-8">
      <title></title>
      <script type="text/javascript">

        //*****************************
        //Sungjuk 이라는 이름의 [생성자 함수] 선언
        //*****************************
        function Sungjuk(stu_no, kor, eng, mat){
          //------------------
          // 속성변수 선언 
          //------------------
          this.stu_no = stu_no;
                this.kor = kor;
                this.eng = eng;
                this.mat = mat;
                //------------------
                // 메소드 선언
                //------------------
                this.getStu_no = function(){
                  // 속성변수 stu_no 안의 데이터를 리턴하기
                    return this.stu_no;
                }
                // 총점을 리턴하는 메소드 선언하기
                this.getTot = function(){
                    // tot 지역변수 선언하고 국,영,수 점수 더하여 저장하기
                    var tot = this.kor + this.eng + this.mat;
                    // tot 지역 변수 안의 데이터를 리턴하기 
                    return tot;
                }
                // 평균을 리턴하는 메소드 선언하기
                this.getAvg = function(){
                  // avg 지역 변수 선언하고 국영수의 평균을 구해 저장하기
                  var avg = Math.ceil(this.getTot()/3);
                  // avg 지역 변수 안의 데이터를 리턴하기 
                  return avg;
                }
                // 학점을 리턴하는 메소드 선언하기
                this.getHakjum = function(){

                  var hakjum = "F";

                  var avg = this.getAvg();

                  if (avg>=90 && avg <=100){
                    hakjum = "A";

                  }else if (avg>=80 && avg <90){
                    hakjum = "B";

                  }else if (avg>=70 && avg <80){
                    hakjum = "C";

                  }else if (avg>=60 && avg <70){
                    hakjum = "D";

                  }

                  return hakjum;
                }


        }



      </script>
    </head>
    <body>
      <script type="text/javascript">
            //-------------------------------
            // [Sungjuk 생성자함수] 객체화 하기
            //-------------------------------
              // 생성자함수 객체화 형식
              //-------------------------------
              //var 객체참조변수명 = new 생성자함수명([데이터]);
              //-------------------------------
            var sungjuk1 = new Sungjuk(1,90,99,70);
            //-------------------------------
              // <1> sungjuk1 이란 변수 선언
              // <2> Sungjuk 이란 생성자 함수를 메모리 공간에 올려 객체화
              // <3> 메모리공간에 올려진 Sungjuk 이란 생성자 함수를 
              // 	   Sungjuk(1,90,99,100) 형식으로 호출
              // <4> Sungjuk 객체의 메모리 위치 주소값을 리턴하여 sungjuk1 변수에 저장
            //-------------------------------
            // Sungjuk 객체의 메소드를 호출하여 얻은 데이터를 출력
            //-------------------------------
            document.write("학번 : " + sungjuk1.getStu_no()+"<br>");
            document.write("총점 : " + sungjuk1.getTot()+"<br>");
            document.write("평균 : " + sungjuk1.getAvg()+"<br>");
            document.write("학점 : " + sungjuk1.getHakjum()+"<hr>");

        //-------------------------------
            // [Sungjuk 생성자함수]를 객체화하기
            //-------------------------------
          var sungjuk2 = new Sungjuk(2,99,98,77);

          //-------------------------------
            // [Sungjuk 생성자함수]를 객체화하기
            //-------------------------------
          var sungjuk3 = new Sungjuk(3,66,77,88);

          //-------------------------------
          // Sungjuk 객체의 메위주를 저장할 Array 객체 생성 
          //-------------------------------
          var sungjukArr = [];

          //-------------------------------
          // Array 객체의 3개의 Sungjuk 객체의 메모리 위치 주소값을 저장 
          //-------------------------------
          sungjukArr.push(sungjuk1);
          sungjukArr.push(sungjuk2);
          sungjukArr.push(sungjuk3);

          //-------------------------------
          // 200개의 Sungjuk 객체를 생성하여 Array 객체 저장하기
          //-------------------------------
          for(var i = 0; i<=200; i++){
            //랜덤한 국어졈수, 영어점수, 수학점수 구하기
            // 랜덤한 점수의 범위는 0~100 사이이다.
            var kor_tmp = Math.ceil(Math.random()*100);
            var eng_tmp = Math.ceil(Math.random()*100);
            var mat_tmp = Math.ceil(Math.random()*100);
            //Sungjuk객체 생성하여 Array 객체에 저장하기 
            sungjukArr.push(

              new Sungjuk(sungjukArr.length+1, kor_tmp, eng_tmp, mat_tmp)
              );
          }


          //-------------------------------
          // Array 객체 안의 배열변수에 저장된 Sungjuk 객체의 순서를 평균에 따라 내림차순으로 바꾸기
          // 즉 평균이 높은 Sungjuk 객체의 메위주를 맨앞 배열변수로 옮기기
          //-------------------------------
          for(var i = 0; i<sungjukArr.length-1; i++){
            for(var j=i+1; j<sungjukArr.length; j++){

              //-------------------------------
              // i번째 배열변수에 저장된 Sungjuk 객체의 평균 얻기 
              // i번째 Sungjuk 국어점수 얻기
              // i번째 Sungjuk 영어점수 얻기
              // i번째 Sungjuk 수학점수 얻기 
              //-------------------------------
              var avg1 = sungjukArr[i].getAvg();
              var kor1 = sungjukArr[i].kor;
              var eng1 = sungjukArr[i].eng;
              var mat1 = sungjukArr[i].mat;

              //-------------------------------
              // j번째 배열변수에 저장된 Sungjuk 객체의 평균 얻기
              // j번째 Sungjuk 국어점수 얻기
              // j번째 Sungjuk 영어점수 얻기
              // j번째 Sungjuk 수학점수 얻기 
              //-------------------------------
              var avg2 = sungjukArr[j].getAvg();
              var kor2 = sungjukArr[j].kor;
              var eng2 = sungjukArr[j].eng;
              var mat2 = sungjukArr[j].mat;

                //-------------------------------
                // 만약 i번째 배열변수에 저장된 Sungjuk 객체의 평균,국어,영어,수학점수와
                //     j번째 배열변수에 저장된 Sungjuk 객체의 평균,국어,영어,수학점수를 비교하여
                //     i번째 배열변수에 저장된 Sungjuk 객체의 메위주와
                // 	   j번째 배열변수에 저장된 Sungjuk 객체의 메위주를 바꾸기
                //-------------------------------
                //flag 변수에 false 저장하기 
                var flag = false;
                // 만약에 i번째 평균이 j번째 평균보다 작다면 flag 변수에 true 저장하기
                if(avg1<avg2){

                  flag = true;
                // 만약에 i번째 평균이 j번째 평균과 같으면서 
                }else if(avg1==avg2){
                  // i번째 국어점수가 j번째 국어점수보다 작으면 flag 변수에 true 저장하기
                  if(kor1<kor2){
                    flag = true;
                  }
                  // i번째 국어점수와 j번째 국어점수가 같으면서 
                  // i번째 영어점수가 j번째 영어점수보다 작으면 flag 변수에 true 저장하기
                  if(kor1==kor2&&eng1<eng2){
                    flag = true;
                  }
                  // i번째 국어점수와 j번째 국어점수가 같고
                  // i번째 영어점수와 j번째 영어점수가 같고 
                  // i번째 수학점수가 j번째 수학점수보다 작으면 flag 변수에 true 저장하기
                  if(kor1==kor2&&eng1==eng2&&mat1<mat2){
                    flag = true;
                  }
                }
                // 만약 flag 변수에 true가 저장되어 있으면
                // i번째 배열변수에 저장된 Sungjuk 객체 메위주와 
                // j번째 배열변수에 저장된 Sungjuk 객체 메위주를 바꾸기
                if(flag==true){
                  var tmp = sungjukArr[i];
                  sungjukArr[i] = sungjukArr[j];
                  sungjukArr[j] = tmp;
                }
            }
          }


          var tot_avg = 0;
            for(var i=0; i<sungjukArr.length;i++){

              tot_avg = tot_avg + sungjukArr[i].getAvg();

            }
          var tot_avg_avg = Math.ceil(tot_avg/sungjukArr.length);






          //---------------------------------------------
          // 반복문을 사용하여 Array 객체에 저장된 [Sungjuk 객체]의
          // 학생번호, 학생명, 총점, 평균을 모두 출력하기
          //---------------------------------------------
          document.write("<hr>학생성적<hr>");
          document.write("<table border=1 cellspacing=0 cellpadding=5>");
          document.write("<caption>학생 성적 ( 총 " + sungjukArr.length +" 명 / 전체평균 "+tot_avg_avg+" 점 )"+"</caption>");
          document.write("<tr><th>등수<th>학번<th>국어<th>영어<th>수학<th>총점<th>평균<th>전체평균보다");

          for(var i = 0; i<sungjukArr.length; i++){


            //--------------------------
            //i번째 Sungjuk 객체의 평균,국어,영어,수학점수 얻기
            //--------------------------
            var avg1 = sungjukArr[i].getAvg();
            var kor1 = sungjukArr[i].kor;
            var eng1 = sungjukArr[i].eng;
            var mat1 = sungjukArr[i].mat;

            //--------------------------
            // 등수를 저장할 변수 rank 선언하고 0저장하기
            // 등수란 i번째 Sungjuk 객체의 평균보다 큰 다른 [Sungjuk 객체의 개수]+1을 말한다.
            ////rank 변수 만들고 자기의 평균보다 큰 학생의 명수를 구하여 1을 더해 rank 변수 안에 저장하기
            //--------------------------
            var rank = 0;

            //--------------------------
            // i번째 Sungjuk 객체의 평균과 다른 Sungjuk객체의 평균을 비교해서
            // i번째 Sungjuk 객체의 평균보다 큰 놈이 있다면 rank 변수 안의 데이터 1 증가 시키기 
            //--------------------------
            for(var j=0; j<sungjukArr.length;j++){

              //나의 평균일 경우 비교말고 건너 뛰기
              if(i==j){continue;}

              //j번째 Sungjuk 객체의 평균,국어,영어,수학점수 얻기.
              var avg2 = sungjukArr[j].getAvg();
            var kor2 = sungjukArr[j].kor;
              var eng2 = sungjukArr[j].eng;
              var mat2 = sungjukArr[j].mat;

              //i번째 Sungjuk 객체의 평균보다 j번째 Sungjuk 객체의 평균이 크면
              //rank 변수 안의 데이터 1증가 시키기
              if(avg1<avg2){
                rank++;

              }

              //i번째 Sungjuk 객체의 평균과 j번째 Sungjuk 객체의 평균이 같으면서
              else if(avg1==avg2){

                // i번째 국어점수가 j번째 국어점수보다 작으면
                // rank 변수안에 데이터 1 증가 시키기
                if(kor1<kor2){
                  rank++;
                }

                // i번째 국어점수와 j번째 국어점수가 같고
                // i번째 영어점수가 j번째 영어점수보다 작으면
                // rank 변수안에 데이터 1 증가 시키기
                if(kor1==kor2&&eng1<eng2){
                  rank++;
                }

                // i번째 국어점수와 j번째 국어점수가 같고
                // i번째 영어점수와 j번째 영어점수가 같고
                // i번째 수학점수가 j번째 수학점수보다 작으면
                // rank 변수안에 데이터 1 증가 시키기
                if(kor1==kor2&&eng1==eng2&&mat1<mat2){
                  rank++;
                }
              }

            }


            //--------------------------
            // 평균 점수 별로 삽입할 배경색을 저장할 변수선언 하기
            // 학점 별로 bgcolor 변수 안의 색상을 바꾸기
            //--------------------------
            var bgcolor = "white";
            if(avg1>=90){
              bgcolor = "lightblue";
            }else if(avg1>=80){
              bgcolor="lightpink";
            }else if(avg1>=70){
              bgcolor="lightgreen";
            }else if(avg1>=60){
              bgcolor="lightyellow";
            }

            //--------------------------
            // 평균 점수 별로 글자색을 저장할 변수선언 하기
            // 학점 별로 fontcolor 변수 안의 글자 색상을 바꾸기
            //--------------------------
            var fontcolor = "black";
            if(avg1>=90){
              fontcolor = "blue";
            }else if(avg1>=80){
              fontcolor="red";
            }else if(avg1>=70){
              fontcolor="green";
            }else if(avg1>=60){
              fontcolor="orange";
            }

            var avg_avg = (sungjukArr[i].getAvg()) - tot_avg_avg;
            if(avg_avg>0){
              avg_avg = "+"+avg_avg;
            }


            //--------------------------
            //<tr>,<td> 태그 출력하기
            //--------------------------
            //배경색
            document.write("<tr bgcolor="+bgcolor+">");
            //글자색
            // document.write("<tr style='color:"+fontcolor+";''>");
            document.write("<td>"+ (rank+1));
            document.write("<td>"+sungjukArr[i].getStu_no());
            document.write("<td>"+sungjukArr[i].kor);
            document.write("<td>"+sungjukArr[i].eng);
            document.write("<td>"+sungjukArr[i].mat);
            document.write("<td>"+sungjukArr[i].getTot());
            document.write("<td>"+sungjukArr[i].getAvg());
            document.write("<td>"+avg_avg);
            }
            document.write("</table>");

      </script>

    </body>
    </html>










