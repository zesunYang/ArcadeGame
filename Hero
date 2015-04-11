import java.awt.Color;
import java.awt.Graphics2D;

import javax.swing.ImageIcon;


public class Hero extends GameObject implements Drawable, Temporal  {
	

	
	public int prevX = 0;
	public int prevY = 0;
	public int life;
	public boolean moveHorizontally = false;
	
	
	public Hero(int x, int y, DigGame game){
		this.x = x;
		this.y = y;
		this.life=5;
		
		this.setInitialLocation();
		this.color = Color.RED;
		this.game = game;
		this.icon=new ImageIcon(".//Graphics//kakakachu.png");
		

	}
	
	
	
	
	public void dig(){
		float x = (this.x + this.width/2)/this.width;
		float y = (this.y + this.height/2)/this.height;
		
		int a = Math.round(x);
		int b = Math.round(y);
		
		this.game.map[b][a] = 0;
	}
	
	
	
	@Override
	public void update() {
		this.dig();
		this.move();
	}

	@Override
	public void draw(Graphics2D g) {
		g.drawImage(this.icon.getImage(), this.x, this.y, this.height, this.width, null);
	}
	
	public void prevMove(){
		this.x += this.prevX;
		this.y += this.prevY;
	}
	
	public boolean boundHit(){
		boolean rightHit = this.x == this.width * (this.game.column-1) && this.xSpeed>0;
		boolean leftHit = this.x == 0 && this.xSpeed < 0;
		boolean upHit = this.y == 0 && this.ySpeed < 0;
		boolean downHit = this.y == this.height * (this.game.row -1) && this.ySpeed > 0;
	return (rightHit || leftHit || upHit || downHit);
	}
	
	public void curMove(){
		if(this.boundHit()){
			this.xSpeed = 0;
			this.ySpeed = 0;
		}
		this.x += this.xSpeed;
		this.y += this.ySpeed;
		
		
		if (!(this.xSpeed == 0 && this.ySpeed ==0)){
		this.prevX = this.xSpeed;
		this.prevY = this.ySpeed;
		}
	}
	
	public void move(){
		if(this.xSpeed != 0 && this.y % this.height != 0){
			this.prevMove();
		}
		else if(this.ySpeed != 0 && this.x % this.width != 0){
			this.prevMove();
		}
		else{
			this.curMove();
		}
		
	}
	
	
	
	
	
	
}
