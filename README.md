package
{
	import flash.display.Sprite;
	import flash.events.Event;
	import flash.events.KeyboardEvent;
	
	public class paddle extends Sprite
	{
		
		private var velocity:Number;
		private var b:ball;
		
		public function paddle()
		{
			super();
			
			velocity = 0;
			
			this.graphics.beginFill(0x000000);
			this.graphics.drawRect(0,0,200, 30);
			this.y= 350;
			this.addEventListener(Event.ADDED_TO_STAGE, init);
			this.addEventListener(Event.ENTER_FRAME, onEnterFrame);
			this.addEventListener(Event.ENTER_FRAME, onE);
		}//end Paddle
		
		private function onEnterFrame(e:Event):void{
			this.x += velocity;
			
			//simulate friction
			velocity *= .9;
		}//end onEnterFrame
		
		private function init(e:Event):void {
			stage.addEventListener(KeyboardEvent.KEY_DOWN, onKeyDown);
		}//end init
		
		public function onKeyDown(e:KeyboardEvent):void {
			trace(e.keyCode);
			if(e.keyCode == 37) {
				velocity = -5;	
			}//end if left
			if(e.keyCode == 39) {
				velocity = 5;
			}//end if right
		}//end onKeyDown
		
		private function onE(e:Event):void {
			
		}
		
	}
}
