import java.awt.Color;
import java.awt.Graphics2D;

import javax.swing.ImageIcon;


public class weapon extends GameObject implements Drawable, Temporal{
	
	public weapon(DigGame game){

		this.game = game;
		this.x = this.game.hero.x + this.width/4;
		this.y = this.game.hero.y + this.height/4;
		this.icon= new ImageIcon(".//Graphics//mediumB.png");
		
		this.xSpeed = this.game.hero.prevX * 5;
		this.ySpeed = this.game.hero.prevY * 5;
		
		if(this.xSpeed == 0 && this.ySpeed == 0){
			this.xSpeed = 25;
		}
		
		this.setInitialLocation();
		this.color = Color.gray;
		
	}
	
	

	
	
	@Override
	public void update() {
		this.move();
		
	}

	@Override
	public void draw(Graphics2D g) {
//		Ellipse2D d = new Ellipse2D.Double(this.x,this.y, this.width/2, this.height/2);
//		g.setColor(this.color);
//		g.fill(d);
		g.drawImage(this.icon.getImage(), this.x, this.y, this.height-25, this.width-25, null);
	}
	
	public void move(){
		this.x += this.xSpeed;
		this.y += this.ySpeed;
	}
	
	public boolean checkBound(){
		boolean right = this.x > this.game.column * this.width;
		boolean left = this.x < -this.width;
		boolean up = this.y < - this.height;
		boolean down = this.y > this.game.row * this.height;
		return (right || left || up || down);
	}
	

	
}
