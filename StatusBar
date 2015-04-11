import java.awt.Color;
import java.awt.Font;

import javax.swing.JLabel;
import javax.swing.JPanel;


public class StatusBar extends JPanel {
	
	public int pointCount = 0;
	public int lifeCount = 5;
	public int levelCount=1;
	private JLabel life;
	private JLabel point;
	private JLabel level;
	
	public StatusBar(){
		this.life = new JLabel("Life:5");
		life.setFont(new Font("Serif", Font.PLAIN, 32));
		life.setForeground(Color.green);
		this.point = new JLabel("Point:0");
		point.setFont(new Font("Serif", Font.PLAIN, 32));
		point.setForeground(Color.BLUE);
		this.level = new JLabel("Level:1");
		level.setFont(new Font("Serif", Font.PLAIN, 32));
		level.setForeground(Color.magenta);
		this.add(this.life);
		this.add(this.point);
		this.add(this.level);
	}
	
	public void changeLevel(int levels){
		this.levelCount+=levels;
		String text = "Level:"+this.levelCount+"   ";
		this.level.setText(text);
	}
	
	public void changePoint(int points){
		this.pointCount+=points;
		String text = "Point:"+this.pointCount+"   ";
		this.point.setText(text);
	}
	
	public void lossLife(){
		this.lifeCount--;
		String text = "Life:" + this.lifeCount;
		this.life.setText(text);
	}
}
