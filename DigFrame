import java.awt.BorderLayout;
import java.awt.Color;
import java.io.File;

import javax.sound.sampled.AudioSystem;
import javax.sound.sampled.Clip;
import javax.swing.ImageIcon;
import javax.swing.JFrame;
import javax.swing.JOptionPane;
import javax.swing.JPanel;


public class DigFrame extends JFrame {
	private int width = 45;
	private int height = 45;
	private JPanel panel;
	public boolean gameVisable=true;
	private DigGame game;
	private boolean die=false;
	private Clip clip;
	
	public DigFrame(StatusBar status,DigGame game){
		this.game = game;
		this.setSize(this.width* this.game.getColumn()+18, this.height * game.getRow()+95);
		this.setBackground(Color.yellow);
		//initialize panel
		
		this.add(new DigComponent(this.game));
		checkdie();
		checkmusic();
	
		this.setTitle("Pikachu");
		this.add(status,BorderLayout.NORTH);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		this.setVisible(gameVisable);

	}
	
	public void checkdie(){
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						
						Thread.sleep((long) 30);
						if (game.status.lifeCount==0){
							die=true;
							dispose();
							clip.close();
							JOptionPane.showMessageDialog(getParent(),new ImageIcon(".//Graphics//pikachew.jpg"));
							
							break;
						}

					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();
		
	}
//	public void showmessage(){
//			JOptionPane.showMessageDialog(getParent(),"Printing complete");
//	}
	public void play() {
		try {
			this.clip = AudioSystem.getClip();
			clip.open(AudioSystem.getAudioInputStream(new File(
					".\\src\\Psyduck.wav")));
			clip.start();
			while (!clip.isRunning())
			    Thread.sleep(10);
			while (clip.isRunning())
			    Thread.sleep(10);
			clip.close();
		} catch (Exception exc) {
			exc.printStackTrace(System.out);
		}
		
	}
	
	public void checkmusic(){
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						
						Thread.sleep((long) 30);
						if (game.status.lifeCount>0){
							die=false;
							play();
							break;
						}
//						play();
//						break;
					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();
	
}}
