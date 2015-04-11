import java.awt.Color;
import java.awt.Graphics2D;

import javax.swing.ImageIcon;


public class Hobbin extends GameObject implements Drawable, Temporal {
	private double precentage=0.10;
	private boolean status=true;
	public Hobbin(int x, int y, DigGame game){
		this.x = x;
		this.y = y;
		this.setInitialLocation();
		this.color = Color.black;
		this.game = game;
//		if (this.status==true){
//			this.icon = new ImageIcon(".//Graphics//1Haunter.png");
//		}else{
//			this.icon = new ImageIcon(".//Graphics//1Koffing.png");
//		}
		this.icon = new ImageIcon(".//Graphics//1Haunter.png");
		
	}

	@Override
	public void update() {
		this.move();
		this.dig();
		this.killHero();
		this.getKilled();
//		this.makechange();
	}

	@Override
	public void draw(Graphics2D g) {
		g.drawImage(this.icon.getImage(), this.x, this.y, this.height, this.width, null);
	}
	
	
	
	
	public void killHero(){
		int xDiff = Math.abs(this.x - this.game.hero.x);
		int yDiff = Math.abs(this.y - this.game.hero.y);
		
		if(xDiff < this.width/1.25 && yDiff< this.height/1.25){
			this.game.status.lossLife();
			this.game.reset();
		}
	}
	
	
	
	public void dig(){
		float x = (this.x + this.width/2)/this.width;
		float y = (this.y + this.height/2)/this.height;
		
		int a = Math.round(x);
		int b = Math.round(y);
		if (a>=20){
			a=19;
		}
		if (b>=19){
			b=19;
		}
		this.game.map[b][a] = 0;
	}
	
	public void move(){
		this.setPath();
		this.x += this.xSpeed;
		this.y += this.ySpeed;
		if (this.y>=(this.game.column-1)*this.height){
			this.y=(this.game.column-1)*this.height;
		}
		if (this.x>=(this.game.row-1)*this.width){
			this.x=(this.game.row-1)*this.width;
		}
	}
	
	public int findPath(){
		
		if(this.x % this.width !=0 || this.y % this.height !=0){
			return 4;
		}
	
		int xDiff = Math.abs(this.x - this.game.hero.x);
		int yDiff = Math.abs(this.y - this.game.hero.y);

		if( xDiff > yDiff){
			if (this.x < this.game.hero.x){
				return 0;
			}
			return 1;
		}
		if(this.y < this.game.hero.y){
			return 2;
		}
		return 3;
	
	
	}
	
	public void setPath(){
		int path = this.findPath();
		if (path == 4){
			return;
		}
		else if (path == 0){
			this.xSpeed = 4;
			this.ySpeed = 0;
		}
		else if (path == 1){
			this.xSpeed = -4;
			this.ySpeed = 0;
		}
		else if (path == 2){
			this.xSpeed = 0;
			this.ySpeed = 4;
		}
		else if (path == 3){
			this.xSpeed = 0;
			this.ySpeed = -4;
		}
	}
	
	
	
	public void getKilled(){
		for(weapon w : this.game.weapons){
			int xCenter = w.x + w.width/4;
			int yCenter = w.y + w.height/4;
			int thisXcenter = this.x + this.width/2;
			int thisYcenter = this.y + this.height/2;
			int xdiff = Math.abs(xCenter - thisXcenter);
			int ydiff = Math.abs(yCenter - thisYcenter);
			
			if(xdiff < this.width && ydiff < this.height){
				this.isDead = true;
				this.reset();
				System.out.println("killed");
			}
		}
		
		for (Gold w: this.game.golds){
			if (this.x==w.x && this.y-w.y<=this.height/1.25 && this.y-w.y>0){
				this.isDead = true;
				this.reset();
			}
				
		}
	}

//	public void makechange() {
//		// TODO Auto-generated method stub.
//		double a = Math.random();
//		if (a<this.precentage){
//			this.status=false;
//			
//		}
//		
//	}
	
	
}
