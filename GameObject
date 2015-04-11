import java.awt.Color;

import javax.swing.ImageIcon;


public abstract class GameObject {
	protected int x;
	protected int y;
	protected int xSpeed;
	protected int ySpeed;
	
	protected int initialX;
	protected int initialY;
	protected ImageIcon icon;
	
	protected int height = 45;
	protected int width = 45;
	protected DigGame game;
	protected Color color;
	protected boolean isDead = false;
	
	
	
	public void reset(){
		this.x = this.initialX;
		this.y = this.initialY;
	}
	
	public void setInitialLocation(){
		this.initialX = this.x;
		this.initialY = this.y;
	}
	
	public int getX(){
		return this.x;
	}
	
	public int getY(){
		return this.y;
	}
	
	public int getXspeed(){
		return this.xSpeed;
	}
	
	public int getYspeed(){
		return this.ySpeed;
	}
	
}
