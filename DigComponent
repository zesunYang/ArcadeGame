import java.awt.Color;
import java.awt.Graphics;
import java.awt.Graphics2D;

import javax.swing.ImageIcon;
import javax.swing.JComponent;

public class DigComponent extends JComponent {

	private static final int FRAMES_PER_SECOND = 30;
	private static final long REPAINT_INTERVAL_MS = 1000 / FRAMES_PER_SECOND;
	private int width = 45;
	private int height = 45;
	private ImageIcon icon;
	private ImageIcon backIcon;

	public DigGame game;

	public DigComponent(DigGame game) {
		this.game = game;
		this.icon = new ImageIcon(".//Graphics//wall.png");
		this.backIcon = new ImageIcon(".//Graphics//Black.png");
		this.setBackground(Color.black);

		this.setFocusable(true);
		this.setSize(game.getColumn() * this.width, game.getRow() * this.height);

		this.addKeyListener(new DigListener(this));
		System.out.println("add");

		Runnable repainter = new Runnable() {
			@Override
			public void run() {
				// Periodically asks Java to repaint this component
				try {
					while (true) {
						Thread.sleep(REPAINT_INTERVAL_MS);
						repaint();
					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(repainter).start();
	}

	@Override
	protected void paintComponent(Graphics g2) {
		super.paintComponent(g2);
		Graphics2D g = (Graphics2D) g2;
		g.drawImage(this.backIcon.getImage(), 0, 0, 1000, 1000, null);
		for (int i = 0; i < this.game.row; i++) {
			for (int j = 0; j < this.game.column; j++) {
				if (this.game.map[i][j] == 1) {
					this.drawDirt(j * this.width, i * this.height, g);
				}
			}
		}
		for (Hobbin hob : this.game.hobbins) {
			hob.draw(g);
		}
		for (Nobbin nob : this.game.nobbins) {
			nob.draw(g);
		}
		for (Gold go : this.game.golds) {
			go.draw(g);
		}
		for (Emerald e : this.game.emeralds) {
			e.draw(g);
		}
		for (weapon e : this.game.weapons) {
			e.draw(g);
		}
		this.game.hero.draw(g);
	}

	public void drawDirt(int x, int y, Graphics2D g) {
		g.drawImage(this.icon.getImage(), x, y, this.height, this.width, null);
	}

	public void drawBackground(Graphics2D g) {
		g.drawImage(this.backIcon.getImage(), 0, 0, this.height, this.width,null);
	}
}
