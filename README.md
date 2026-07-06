# Inheritance
This program is Based on Inheritance it is made up about details of electric appliances and status of On and Off

class Appliances{
      private String color;
      private final String company;
      private static int countAppliances;
   
     Appliances(String color,String company){
              this.color=color;
              this.company=company;
              countAppliances++;
    }
    String getColor(){
              return color;
   }
   void setColor(String color){
             this.color=color;
   }
   String getCompany(){
              return company;
   }
      static int getCountAppliances(){
              return countAppliances;
   }
   
   void turnOn(){
             System.out.println("The electrical Appliances is turn on");
   }
   void turnOff(){
            System.out.println("The electrical Appliances is turn off");
   }
}

class Fan extends Appliances{
       int speed ;
       int noOfWings;
     
       Fan(String color,String company,int speed,int noOfWings){
           super(color,company);
           this.speed=speed;
           this.noOfWings=noOfWings;
      }

      public String toString(){
             return "Color" + getColor()+",Company :" + getCompany() + ",Speed : " + speed +"No of Wings :"+ noOfWings;
      }

     void turnOn(){
           System.out.println("Fan is turned on");
           giveAir();
     }
     void turnOff(){
           System.out.println("Fan is turned off");
     }
     void giveAir(){
           System.out.println("Fan is giving Air");
    }
}
   

 class TubeLight extends Appliances{
           char type; 
        
           TubeLight(String color,String company,char type){
                  super(color,company);
                  this.type=type;
           }
      
           public String toString(){
             return "Color" + getColor()+",Company :" + getCompany() +",Type : " + type ;
           }
          void turnOn(){
                  
                 System.out.println("Tubelight is turned on");
                 giveLight();
          }   
          void turnOff(){
                 System.out.println("Tubelight is turned off");
          }
          void giveLight(){
                 System.out.println("Tubelight is glowing");
          }
 }

 class Switch{
         
         private String color;
         private boolean status;
         private static int countSwitch;
         private Appliances appliances;
  
        Switch(String color,boolean status,Appliances appliances){
                 this.color=color;
                 this.status=status;
                 this.appliances=appliances;
                 countSwitch++;
       }
            
       public String toString(){
             return "Color" + color+",Status : " + status;
       }
       static int getCountSwitch()
	{
		return countSwitch;
	}
       void press(){
           if(status==true){
                 status=false;
                 appliances.turnOff();
        }else{
                 status=true;
                 appliances.turnOn();
        }
     }          

  }

class InheritanceDemo{
             public static void main(String args[]){
            
             
		Fan fan1 = new Fan("Brown","Orient",5,3);
		TubeLight tube1 = new TubeLight("White","Phillips",'F');

		System.out.println(fan1);
		System.out.println(tube1);

		Switch s1 = new Switch("White",false,fan1);
		Switch s2 = new Switch("White",false,tube1);

		System.out.println(s1);
		System.out.println(s2);

		System.out.println("No. of Appliances: "+Appliances.getCountAppliances());
		System.out.println("No. of Switches: "+Switch.getCountSwitch());

		s1.press();
		s2.press();

		System.out.println(s1);
		System.out.println(s2);		
	}
}
    
