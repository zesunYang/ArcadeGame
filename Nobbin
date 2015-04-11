import java.awt.Color;

import javax.swing.ImageIcon;

public class Nobbin extends Hobbin implements Drawable, Temporal {

	public String direction;
	private double precentage=0.10;
	private boolean orginal=true;
	public Nobbin(int x, int y, DigGame game) {
		super(x, y, game);
		this.color = Color.green;
		this.setInitialLocation();
//		this.makechange();
//		if (this.orginal==true){
//			this.icon = new ImageIcon(".//Graphics//1Koffing.png");
//		}else{
//			this.icon = new ImageIcon(".//Graphics//1Haunter.png");
//		}
		this.icon=new ImageIcon(".//Graphics//1Koffing.png");

	}

	@Override
	public int findPath() {
		return 0;
		// nothing
	}

	@Override
	public void setPath() {
		// nothing
	}

	 @Override
	 public void dig() {
	 // nothing
	 }

	public int[][] makeThePathMap() {
		int[][] tempArray = new int[this.game.row][this.game.column];
		for (int i = 0; i < this.game.row; i++) {
			for (int j = 0; j < this.game.column; j++) {
				if (this.game.map[i][j] > 1) {
					tempArray[i][j] = -1;
				}
				if (this.game.map[i][j] > 0) {
					tempArray[i][j] = -1;
				}
			}
		}
		return tempArray;
	}

	public int[][] findNobbinPath() {
		// finds quickest path to hero
		int[][] tempArray = makeThePathMap();
		tempArray[this.y / 45][this.x / 45] = 0;
		tempArray[this.game.hero.y / 45][this.game.hero.x / 45] = 1;
		while (tempArray[this.y / 45][this.x / 45] == 0) {
			// System.out.println("1");
			for (int t = 0; t < this.game.row; t++) {
				// System.out.println("2");
				for (int m = 0; m < this.game.column; m++) {
					// System.out.println("3");
					if (tempArray[t][m] > 0) {
						// System.out.println("4");
						if (t + 1 < 20) {
							// System.out.println("5");
							if (tempArray[t + 1][m] == 0) {
								tempArray[t + 1][m] = tempArray[t][m] + 1;
							}
						}
						if (t - 1 >= 0) {
							// System.out.println("6");
							if (tempArray[t - 1][m] == 0) {
								tempArray[t - 1][m] = tempArray[t][m] + 1;
							}
						}
						if (m + 1 < 20) {
							// System.out.println("7");
							if (tempArray[t][m + 1] == 0) {
								tempArray[t][m + 1] = tempArray[t][m] + 1;
							}
						}
						if (m - 1 >= 0) {
							// System.out.println("8");
							if (tempArray[t][m - 1] == 0) {
								tempArray[t][m - 1] = tempArray[t][m] + 1;
							}
						}
					}
				}
			}
		}
		return tempArray;
	}

	public void setNobbinPath() {
		int[][] path = this.findNobbinPath();
		int actualY = (this.y) / 45;
		int actualX = (this.x) / 45;
		int currentValue = path[actualY][actualX];
		if (actualX + 1 < 20) {
			if (currentValue - 1 == path[actualY][actualX + 1]
					&& path[actualY][actualX + 1] > 0) {
				if(this.x % this.width == 0 && this.y % this.height == 0){
					this.xSpeed = 5;
					this.ySpeed = 0;
					currentValue--;
				}
			}
		}
		if (actualX - 1 >= 0) {
			if (currentValue - 1 == path[actualY][actualX - 1]
					&& path[actualY][actualX - 1] > 0) {
				if(this.x % this.width == 0 && this.y % this.height == 0){
					this.xSpeed = -5;
					this.ySpeed = 0;
					currentValue--;
				}
			}
		}
		if (actualY + 1 < 20) {
			if (currentValue - 1 == path[actualY + 1][actualX]
					&& path[actualY + 1][actualX] > 0) {
				if(this.x % this.width == 0 && this.y % this.height == 0){
					this.xSpeed = 0;
					this.ySpeed = 5;
					currentValue--;
				}
			}
		}
		if (actualY - 1 >= 0) {
			if (currentValue - 1 == path[actualY - 1][actualX]
					&& path[actualY - 1][actualX] > 0) {
				if(this.x % this.width == 0 && this.y % this.height == 0){
					this.xSpeed = 0;
					this.ySpeed = -5;
					currentValue--;
				}
			}
		}
	}

	@Override
	public void move() {
		this.setNobbinPath();
		this.x += this.xSpeed;
		this.y += this.ySpeed;
	}
	
//	public void makechange(){
//		double a = Math.random();
//		if (a<this.precentage){
//			this.orginal=false;
//			
//		}
//	}

}

