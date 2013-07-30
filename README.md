package
{
  import flash.display.Sprite;
	import flash.events.Event;
	
	public class ball extends Sprite
	{
		
		public var velocity:Object;
		public var acceleration:Object;
		public var bounciness:Number;
		
		public function ball(targBounciness:Number)
		{
			super();
			//set our bounciness
			bounciness = targBounciness;
			
			//make a circle around the middle of the
			//sprite
			this.graphics.beginFill(Math.random() * 0xFFFFFF);
			this.graphics.drawCircle(0,0, 40);
			
			//setup velocity
			velocity = {};
			velocity.x = Math.random() * 5;
			velocity.y = 20;
			
			//setup acceleration
			acceleration = new Object();
			acceleration.x = 0;
			acceleration.y = 1;
			
			this.addEventListener(Event.ENTER_FRAME, onEnterFrame);
		}
		
		public function onEnterFrame(e:Event):void {
			
			this.velocity.x += this.acceleration.x;
			this.velocity.y += this.acceleration.y;
			
			this.x += this.velocity.x;
			this.y += this.velocity.y;
			
			if(this.y < 0) {
				this.y = 0;
				this.velocity.y *= -1;
			}
			
			if(this.x < 0) {
				this.x = 0;
				this.velocity.x *= -1;
			}
			
			if(this.x > stage.stageWidth) {
				this.x = stage.stageWidth;
				this.velocity.x *= -1;
			}
			
			if(this.y > stage.stageHeight) {
				this.y = stage.stageHeight;
				this.velocity.y *= -bounciness;
				this.velocity.x *= bounciness;
			}
		}
	}
}
