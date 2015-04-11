import java.io.File;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Scanner;

public class DigGame {
	public int row = 20;
	public int column = 20;
	private int height = 45;
	private int width = 45;
	public StatusBar status;
	public int orgEmerald = 0;
	static float UPDATE_INTERVAL_MS = 30;
	static double GAME_FPS = 1000 / UPDATE_INTERVAL_MS;

	public int[][] map = new int[this.column + 1][this.row];
	public ArrayList<Emerald> emeralds = new ArrayList<Emerald>();
	public ArrayList<Gold> golds = new ArrayList<Gold>();
	public ArrayList<Nobbin> nobbins = new ArrayList<Nobbin>();
	public Hero hero = new Hero(0, 0, this);
	public ArrayList<Hobbin> hobbins = new ArrayList<Hobbin>();
	public ArrayList<weapon> weapons = new ArrayList<weapon>();

	public DigGame(StatusBar status) throws IOException {
		this.status = status;
		this.initialize();
		this.addHeroThread();
		this.addEmeraldThread();
		this.addHobbinThread();
		this.addNobbinThread();
		this.addWeaponThread();
		this.addGoldThread();
		this.checkEmer();
		

	}

	public void reset() {
		this.weapons.clear();

		for (Nobbin n : this.nobbins) {
			n.reset();
		}
		for (Hobbin n : this.hobbins) {
			n.reset();
		}
		this.hero.reset();
	}

	public void initialize() throws FileNotFoundException {
		this.hobbins.clear();
		this.nobbins.clear();
		this.emeralds.clear();
		this.golds.clear();
		this.weapons.clear();

		String _level = ".//src//level" + this.status.levelCount;
		this.readFile(_level);

	}

	public void upLevel() throws FileNotFoundException {
		if (this.status.levelCount < 3) {
			this.status.changeLevel(1);
			this.initialize();
		}
	}

	public void downLevel() throws FileNotFoundException {
		if (this.status.levelCount > 1) {
			this.status.changeLevel(-1);
			this.initialize();
		}
	}

	public void addWeapon() {
		weapon w = new weapon(this);
		this.weapons.add(w);
	}

	public void addWeaponThread() {
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						Thread.sleep((long) GAME_FPS);
						for (weapon w : DigGame.this.weapons) {
							w.update();
						}
						// System.out.println("???");
					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();
	}

	public void addHeroThread() {
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						Thread.sleep((long) GAME_FPS);
						DigGame.this.hero.update();
						// System.out.println("???");
					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();
	}

	public void addEmeraldThread() {
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						Thread.sleep((long) GAME_FPS);
						for (Emerald e : DigGame.this.emeralds) {
							e.update();
						}
					}
				} catch (Exception exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();
	}

	public void addHobbinThread() {
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						Thread.sleep((long) GAME_FPS);
						for (Hobbin e : DigGame.this.hobbins) {
							e.update();
						}
					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();
	}

	public void addNobbinThread() {
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						Thread.sleep((long) GAME_FPS);
						for (Nobbin e : DigGame.this.nobbins) {
							e.update();
						}
					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();
	}

	public void addGoldThread() {
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						Thread.sleep((long) GAME_FPS);
						for (Gold e : DigGame.this.golds) {
							e.update();
						}
					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();
	}

	public void readFile(String file) throws FileNotFoundException {
		File inputFile = new File(file);
		Scanner inScanner = new Scanner(inputFile);
		int row1 = 0;
		while (inScanner.hasNextLine()) {
			String temp = inScanner.nextLine();
			for (int i = 0; i < 20; i++) {
				this.map[row1][i] = Integer.parseInt(Character.toString(temp
						.charAt(i)));
				if (this.map[row1][i] != 0) {

					if (this.map[row1][i] == 2) {

						this.hero.x = this.width * i;
						this.hero.y = this.height * row1;
						this.hero.initialX = this.hero.x;
						this.hero.initialY = this.hero.y;
					} else if (this.map[row1][i] == 3) {
						Hobbin hob = new Hobbin(this.width * i, this.height
								* row1, this);
						this.hobbins.add(hob);
					} else if (this.map[row1][i] == 4) {
						Nobbin nob = new Nobbin(this.width * i, this.height
								* row1, this);
						this.nobbins.add(nob);
					} else if (this.map[row1][i] == 5) {
						Gold gold = new Gold(this.width * i,
								this.height * row1, this);
						this.golds.add(gold);
					} else if (this.map[row1][i] == 6) {
						Emerald emerald = new Emerald(this.width * i,
								this.height * row1, this);
						this.emeralds.add(emerald);
						this.orgEmerald++;
					}
					this.map[row1][i] = 1;
				}
			}
			row1++;
		}
		for (int i = 0; i < this.column; i++) {
			this.map[row1][i] = 1;
		}
		inScanner.close();
	}

	public int getRow() {
		return this.row;
	}

	public int getColumn() {
		return this.column;
	}

	public void checkEmer() {
		Runnable run = new Runnable() {
			@Override
			public void run() {
				try {
					while (true) {
						Thread.sleep((long) GAME_FPS);
						if (orgEmerald == 0) {
							try {
								upLevel();
							} catch (FileNotFoundException exception) {
								// TODO Auto-generated catch-block stub.
								exception.printStackTrace();
							}
						}
					}
				} catch (InterruptedException exception) {
					// Stop when interrupted
				}
			}
		};
		new Thread(run).start();

	}

}
