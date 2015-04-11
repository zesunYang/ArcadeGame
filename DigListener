import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.io.FileNotFoundException;


public class DigListener implements KeyListener {
	
	private DigComponent component;
	private Hero hero;
	private int speed = 5;
    private boolean keyPressed = false;
	
	public DigListener(DigComponent component){
		this.component = component;
		this.hero = this.component.game.hero;
	}
	
	@Override
	public void keyPressed(KeyEvent e) {
		if (this.keyPressed){
			return ;
		}
		
		this.keyPressed = true;
		switch (e.getKeyCode()) {
			
			case KeyEvent.VK_LEFT: 
				this.hero.xSpeed = -this.speed;

				
				break;
			case KeyEvent.VK_RIGHT:
				this.hero.xSpeed = this.speed;

				break;
				
			case KeyEvent.VK_DOWN:
				this.hero.ySpeed = this.speed;

				break;
				
			case KeyEvent.VK_UP:
				this.hero.ySpeed = -this.speed;
	
				break;
			case KeyEvent.VK_U:
			try {
				this.component.game.upLevel();
			} catch (FileNotFoundException exception) {
				
				exception.printStackTrace();
			}
				break;
				
			case KeyEvent.VK_D:
				try {
					this.component.game.downLevel();
				} catch (FileNotFoundException exception) {
					
					exception.printStackTrace();
				}
					break;
			case KeyEvent.VK_R:
				this.component.game.reset();
				break;
			case KeyEvent.VK_SPACE:
				this.component.game.addWeapon();
				
			default:
				return;
			
		
		}
		
	}

	@Override
	public void keyReleased(KeyEvent e) {
		this.hero.xSpeed = 0;
		this.hero.ySpeed = 0;
		
		this.keyPressed = false;

		
	}

	@Override
	public void keyTyped(KeyEvent e) {
		// TODO Auto-generated method stub.
		
	}

}
