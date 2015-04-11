import java.awt.BorderLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.FileNotFoundException;
import java.io.IOException;

import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;


public class StartFrame extends JFrame{
	private int width = 45;
	private int height = 45;
	private JPanel panel;
	private DigGame game;
	private JButton startB;
	private boolean introvalue=true;
	
	public StartFrame() throws IOException{
		this.setSize(918, 995);
		panel=new JPanel();
		panel.add(new JLabel(new ImageIcon(".\\Graphics\\asdf.png")),BorderLayout.NORTH);
		startB=new JButton("start game");
		StatusBar  status = new StatusBar();
		try {
			game= new DigGame(status);
		} catch (FileNotFoundException exception) {
			// TODO Auto-generated catch-block stub.
			exception.printStackTrace();
		}
//		this.hide();
		startB.addActionListener(new ActionListener() {

			@Override
			public void actionPerformed(ActionEvent e) {
				dispose();
//				StatusBar  status = new StatusBar();
//				DigFrame frame = new DigFrame(new StatusBar(),game);
				StatusBar status = new StatusBar();
				DigGame game;
				try {
					game = new DigGame(status);
					DigFrame frame = new DigFrame(status,game);
				} catch (FileNotFoundException exception) {
					// TODO Auto-generated catch-block stub.
					exception.printStackTrace();
				} catch (IOException exception) {
					// TODO Auto-generated catch-block stub.
					exception.printStackTrace();
				}
				
			}
			
		});
		startB.setSize(20, 20);
		panel.add(startB,BorderLayout.SOUTH);
		this.add(panel);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		this.setVisible(true);
		
	}
}
