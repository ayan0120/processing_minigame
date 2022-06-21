/*
タイルをクリックで消していき、全てのタイルを消す速さを測るゲームです。
何かしらのキーを押すことでゲームがスタートし、タイルはクリックで消えていきます。
タイル一枚消すごとに10点加算されます。
制限時間内に全てのタイルが消せないとゲームオーバーとなります。
制限時間内に全てのタイルが消せると、残り時間が最終得点に加算されます。
*/

/*
参考にしたコードのサイト
「ブロック崩しを作ろう」
https://www.greenowl5.com/gprogram/processing/processing140.html
*/

int score;  //点数
int px = 200;  //自機のX座標
int py = 420;  //自機のY座標
int bx, by;  //球の座標
int blx, bly;  //ブロックの座標
int scSw;  //画面切り替えのスイッチ変数
int[] blsw = new int[20];  //ブロックの当たり判定用スイッチ
int time;  //残り時間

void setup(){
  size(400, 500);
  noStroke();
  colorMode(HSB, 100, 100, 100);
  gameSetting();
}

void draw(){
  background(0);
  if(scSw == 0){
    gameTitle();
  }else if(scSw == 1){
    gamePlay();
  }else if(scSw == 2){
    gameClear();
  }else{
    gameOver();
  }
}


//スタート画面
void gameTitle(){
  textSize(20);
   fill(25, 100, 100);
   text("press the key to start", 92, 250);
}


//ブロック表示をONにする
void gameSetting(){
  for(int i=0; i<20; i++){
    blsw[i]=1;
  }
}


//ゲームのプレイ画面
void gamePlay(){
  block();
  //スコア表示
  textSize(24);
  fill(0, 0, 100);
  text("score:"+score, 10, 25);
  //残り時間表示
  textSize(24);
  fill(0, 0, 100);
  time = 10-millis()/1000;
  text("time:"+time, 150, 25);
  
  //制限時間が0になったらゲームオーバー画面へ
  if(time == 0){
    scSw=3;
  }
  
  //全てのタイルが消せたらクリア画面へ
  if(score==(blsw.length*10)){
    scSw=2;
  }
}


//ゲームオーバー時の画面
void gameOver(){
  textSize(50);
  fill(1, 100, 100);
  text("GAME OVER", 60, 300);  //ゲームオーバーの表示
  
  textSize(25);
  fill(20, 100, 100);
  text("score is "+score, 110, 332);  //最終スコアの表示
}


//ゲームクリア画面
void gameClear(){
  textSize(50);
  fill(50, 100, 100);
  text("GAME CLEAR", 50, 300);  //ゲームクリアの表示
  
  textSize(20);
  fill(20, 100, 100);
  text("score:"+score+"  time:"+time, 100, 332);
  
  textSize(25);
  fill(20, 100, 100);
  text("score is "+(score+time), 110, 360);  //最終スコアの表示
}


//ブロック
void block(){
  blx=50;
  for(int i=0; i<20; i++){
    if(blsw[i]==1){
      if(i<4){
         bly=70;
      }else if(4<=i && i<8){
        bly=110;
      }else if(8<=i && i<12){
        bly=150;
      }else if(12<=i && i<16){
        bly=190;
      }else{bly=230;}
      fill(i*5, 100, 100);
      blx = 50 + (i%4)*80;
      
      if(mousePressed == true){
        if(blx<mouseX && mouseX<blx+80 && bly<mouseY && mouseY<bly+40){
          blsw[i]=0;
          score = score+10;
        }
      }
      if(blsw[i]==1){
        rect(blx, bly, 80, 40, 5);
      }
    }
  }
}


void keyPressed(){
  if(scSw == 0){
    scSw = 1;
  }
}
