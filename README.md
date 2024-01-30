# ch09.html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>문서의 동적 구성</title>
    <script>
        function fn_create() {
            let newDiv = document.createElement("div"); //생성
            let obj = document.getElementById("parent"); //
            newDiv.innerHTML = "새로 생성된 div 입니다.";
            newDiv.setAttribute("class", "myDiv");
            newDiv.style.backgroundColor = 'yellow';
            //버튼 추가
            let btn = document.createElement('button');
            btn.innerHTML = 'x';
            btn.onclick = function () {
                let body = this.parentElement.parentElement; //부모의 부모
                let parent_div = this.parentElement; //부모
                body.removeChild(parent_div);  //조상에서 부모 삭제                
            }
            newDiv.appendChild(btn);
            newDiv.ondblclick = function () {
                //이벤트리스너가 작동될 떄
                //적용한 function에서의 this는 해당 엘리먼트 자신


                obj.removeChild(this);
            }
            obj.appendChild(newDiv);

        }
        function fn_insert() {

            let newDiv = document.createElement("div"); //생성
            let obj = document.getElementById("parent"); //
            newDiv.innerHTML = "새로 생성된 div 입니다.";
            obj.insertBefore(newDiv, obj.childNodes[0]) //하위요소 중 처음위치
        }
    </script>
</head>

<body id="parent">
    <h3>Div 객체를 동적으로 생성, 삽입 ,삭제하는 예제</h3>
    <hr>
    <a href="javascript:fn_create()">Div 생성</a>
    <a href="javascript:fn_insert()">0번째에 추가</a>


</body>

</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>input의 radio</title>
    <script>
        function fn_check(){
            let found = null;
            let citys = document.getElementsByName("city");
            for(i=0; i < citys.length; i++){
                if(citys[i].checked == true){
                    found = citys[i];
                }
            }
            if(found != null){
                alert(found.value+"이 선택됨.");
            }else{
                alert("선택된게 없음.");
                citys[0].focus(); //포커스이동
            }
        }
    </script>
</head>
<body>
    <h3>버튼을 클릭하면 선택하신 라디오 버튼을 value를 출력합니다</h3>
    <hr>
    <from action="#">
        <input type ="radio" name="city" value="seoul">서울
        <input type ="radio" name="city" value="busan">부산
        <input type ="radio" name="city" value="daejean">대전<br>
        <input type ="radio" name="gender" value="F">여자
        <input type ="radio" name="gender" value="M">남자
        <input type ="button" value="선택값 가져오기"onclick="fn_check()">
        <input type ="submit" value="전송">

    </from>
    
</body>
</html>
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>input의 checkbox</title>
</head>

<body>
    <div>
        <h3>취미를 선택하세요</h3>
        <span id="all">
            <label for="">전체 <input type="checkbox" onchange="fn_all(this)"></label>
        </span>
    </div>
    <div>
        <form action="">
            <label for="read">독서<input type="checkbox" id="read" name="hobby" value="read"></label>
            <label for="game">게임<input type="checkbox" id="game" name="hobby" value="game"></label>
            <label for="cook">요리<input type="checkbox" id="cook" name="hobby" value="cook"></label>
            <label for="surf">서핑<input type="checkbox" id="suft" name="hobby" value="surf"></label>
            <input type="button" value="확인" onclick="fn_check()">
            <input type="reset" value="초기화">
            
        </form>
    </div>
    <script>
        function fn_check(){
            let objs = document.getElementsByName("hobby");
            let msg = "당신의 취미는";
            for(let i=0; i<objs.length; i++){
                if(objs[i].checked){
                    msg += objs[i].value + ":" + objs[i].parentElement.innerText + " ";
                }
            }
            alert(msg + "입니다.");
        }
        function fn_all(obj){
            console.log(obj);
            let flag = obj.checked;
            let arr = document.getElementsByName('hobby');
            for(let i=0; i < arr.length; i++){
                arr[i].checked=flag;
            }
        }
    </script>

</body>

</html>
