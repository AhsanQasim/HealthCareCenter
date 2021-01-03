/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package project;


import java.util.*;
import java.io.*;
public class NewClass2 {
    private static File pdata=new File("pdata.txt");
    static String data[][]=new String[100][11];
    static int count12=0;
    public static void main(String[] args)
    {
        Function();
    }
    public static void Function(){
        if(!pdata.exists())
        {
            try {
                pdata.createNewFile();
            } catch (IOException ex) {
                System.out.println(ex);
            }
        }
        
        
        Scanner input=new Scanner(System.in);
        
        
        
        DataEntryFileToArray(data);
        boolean w=true;
        while(w==true)
        {
            System.out.println("===================================================="
                            +"\n              Welcome to Health Care Center"
                            +"\n====================================================");

            System.out.println("(1)=Check Database\n(2)=Sign Up\n(3)=Log In\n(4)=exit");
            int choice=input.nextInt();
            input.nextLine();
            if(choice==1)
            {
                for(int i=0;i<data.length;i++)
                {
                    if(data[i][0]==null)
                    {
                        break;
                    }
                    for(int j=0;j<11;j++)
                    {
                        System.out.print(data[i][j] + "\t\t"
                                + "");
                    }
                    System.out.println("");
                }
            }
                    
            else if(choice==2)
                {
                    int i1=0;
                    for(int k = 0; k<100; k++)
                    {
                        if(data[i1][0]==null)
                            break;
                        if(data[i1][0]!=null)
                            i1++;
                    }
                    System.out.println("====================================================");
                    for(int j=0 ; j < 11 ; j++)
                    {
                        if(j==0)
                        {
                        data[i1][j]=name();
                        }
                        else if(j==1)
                        {
                        data[i1][j]=weight();
                        }
                        else if(j==2)
                        {
                        data[i1][j]=Phone();
                        }
                        else if(j==3)
                        {
                        data[i1][j]=height();  
                        }
                        else if(j==4)
                        {
                        data[i1][j]=age();    
                        }
                        else if(j==5)
                        {
                        data[i1][j]=cnic();    
                        }
                        else if(j==6)
                        {
                        data[i1][j]=address();   
                        }
                        else if(j==7)
                        {
                        data[i1][j]=gender();   
                        }
                        else if(j==8)
                        {
                        data[i1][j]=diseases();   
                        }
                        else if(j==9)
                        {
                        data[i1][j]=familydiseases();   
                        }
                        
                        else if(j==10)
                        {
                        data[i1][j]=password();    
                        }
                        
                    }
                    System.out.println("====================================================");
                    //i1++;
                    Arraytofileconversion(data);
            }
            else if(choice==3)
            {
                int H=0;
                int count=0;
                System.out.println("Enter Name");
                String name=input.nextLine();
                for(int i=0;i<data.length;i++)
                {
                    if(name.equals(data[i][0]))
                    {
                        H=i;
                        
                        System.out.println("                   ACCOUNT FOUND\n");
                        
                        System.out.println("Enter Password");
                        String pass=input.nextLine();
                        if(data[i][10].equals(pass))
                        {
                            System.out.println("****************************************************");
                            System.out.println("           You have entered your account");
                            System.out.println("****************************************************");
                            count=1;
                            break;
                        }
                    }
                }
                if(count==1)
                {
                    boolean I=true;
                    while(I==true)
                   {
                       System.out.println("Enter (1).Check Ideal Weight.\n"+
                                          "(2).Check Ideal Calories\n"+
                                          "(3).Check Body Mass Index\n"+
                                          "(4).Get Appointment with Doctor\n"+
                                          "(5).Check Doctor's Detali\n"+
                                          "(6).Check Symptoms of diseases\n"+
                                          "(7).Buy Medicines\n"+
                                          "(8).Exit");
                       System.out.println("****************************************************");
                       int c=choice();
                       if(c==1)
                       {
                           double height1;
                           height1=Double.parseDouble(data[H][3]);
                           String gender1=data[H][7];
                           idealweight(height1,gender1);
                       }
                       else if(c==2)
                       {
                           double height1=Double.parseDouble(data[H][3]);
                           String gender1=data[H][7];
                           double age1=Double.parseDouble(data[H][4]);
                           double weight1=Double.parseDouble(data[H][1]);
                           idealcalorie(height1,gender1,age1,weight1);
                       }
                       else if(c==3)
                       {
                           double height1=Double.parseDouble(data[H][3]);
                           double weight1=Double.parseDouble(data[H][1]);
                           bodymassindex(height1,weight1);
                       }
                       else if(c==4)
                       {
                           appointments();
                       }
                       else if(c==5)
                       {
                           drdetails();
                       }
                       else if(c==6)
                       {
                           symptoms();
                       }
                       else if(c==7)
                       {
                           medicines(); 
                       }
                       else if(c==8)
                       {
                           I=false;  
                       }
                       else
                       {
                           System.out.println("invalid entry");
                       }
                           
                   }
                       
                }
            }
            else if(choice==4)
            {
                w=false;
            }
            else
            {
                System.out.println("Invalid Entry");
            }
        }   
    }
    public static String name() 
    { 
        Scanner input=new Scanner(System.in);
        input.nextLine();
        System.out.println("Enter Patient Name");
        String x=input.nextLine(); 
        for(int i=0;i<count12;i++)
        {
            if(data[i][0].equals(x))
            {
                System.out.println("Account already exists on this name");
                System.out.println("Enter Patient Name");
                x=input.nextLine();
                break;
            }
        }
        count12++;
        System.out.println("______________________________");
        return x;
    } 
     
    public static String password() 
    { 
        Scanner input=new Scanner(System.in);
        System.out.println("Enter Password");
        String temp1=input.nextLine(); 
        System.out.println("______________________________");
        return temp1; 
      
    } 
    public static String gender() 
    { 
        Scanner input=new Scanner(System.in);
        boolean n=false;
        String x=null;
        System.out.println("enter male or female");
        while(n==false)
        {
            
            System.out.println("Enter Patient Gender"); 
            x=input.nextLine();
            
            if(x.equals("male")||x.equals("female"))
            {
                n=true;
            }
            else
            {
                System.out.println("invalid entry"); 
            }
        }
        System.out.println("______________________________");
        
        return x; 
        
    } 
     
     
    public static String address() 
    { 
        Scanner input=new Scanner(System.in);
        System.out.println("Enter Patient Adress");
        String x=input.nextLine();
        System.out.println("______________________________");
        return x; 
    } 
     
    public static String cnic() 
    { 
        Scanner input=new Scanner(System.in);
        System.out.println("Enter Patient CNIC");
        long x=0; 
        try 
        { 
            x=input.nextLong(); 
        } 
        catch(Exception e) 
        { 
            System.out.println("an integer is required"); 
        } 
        String Temp1=Long.toString(x); 
        System.out.println("______________________________");
        return Temp1; 
        
    } 
     
    public static int choice() 
    { 
        Scanner input=new Scanner(System.in); 
        int x=0; 
        try 
        { 
             x=input.nextInt(); 
        } 
        catch(Exception e) 
        { 
            System.out.println("An interger is required."); 
        } 
        System.out.println("______________________________");
        return x; 
        
    } 
     
    public static String Phone() 
    { 
        long x=0;
        String temp1=null;
        while(true)
        {
            try
            {
        
                Scanner input=new Scanner(System.in);
                System.out.println("Enter Patient Contact Number\n Enter number in integer");
                x=input.nextLong();
                temp1=Long.toString(x);
                break;
            }
            catch(Exception e)
            {
                System.out.println("Invalid");
            
            }
        }
        System.out.println("______________________________");
        return temp1; 
        
    } 
     
    public static String weight() 
    { 
        Scanner input=new Scanner(System.in);
        System.out.println("Enter Patient Weight");
        double x=0; 
        try 
        { 
             x=input.nextDouble(); 
        } 
        catch(Exception e) 
        { 
            System.out.println("An double is required."); 
        } 
        String temp1=Double.toString(x);
        System.out.println("______________________________");
        return temp1; 
        
    } 
     
    public static String height() 
    { 
        Scanner input=new Scanner(System.in);
        System.out.println("Enter Patient Height(Inches)"); 
        int x=0; 
        try 
        { 
             
            x=input.nextInt(); 
        } 
        catch(Exception e) 
        { 
            System.out.println("An integer is required."); 
        } 
        String temp1=Integer.toString(x);
        System.out.println("______________________________");
        return temp1; 
        
    } 
     
    public static String age() 
    { 
        Scanner input=new Scanner(System.in);
        System.out.println("Enter Patient Age");
        int x=0; 
        try 
        { 
            x=input.nextInt(); 
        } 
        catch(Exception e) 
        { 
            System.out.println("An integer is required."); 
        }
        String temp1=Integer.toString(x);
        System.out.println("______________________________");
        return temp1; 
        
    } 
    public static String diseases() 
    { 
        Scanner input=new Scanner(System.in);
        System.out.println("Enter Patient Disease");
        String x=input.nextLine(); 
        System.out.println("______________________________");
        return x; 
    } 
    public static String familydiseases() 
    { 
        Scanner input=new Scanner(System.in); 
        System.out.println("Enter Patient Family Disease");
        String x=input.nextLine(); 
        
        return x; 
    }
    public static void idealweight(double hig,String gen) 
    { 
        if(gen.equals("female")) 
        { 
            if(hig>60) 
            { 
            double c=hig-60; 
            double ans=53.1; 
            for(int i=1;i<=c;i++) 
            { 
                ans=ans+1.36; 
            } 
            System.out.println("Ideal weight according to  Robinson formula (1983) is"+ans); 
            System.out.println("______________________________");
                  
            } 
        } 
        if(gen.equals("male")) 
        { 
            if(hig>60) 
            { 
            Double c=hig-60; 
            double ans=53.1; 
            for(int i=1;i<=c;i++) 
            { 
                ans=ans+1.41; 
            } 
            System.out.println("Ideal weight according to  Robinson formula (1983) is"+ans); 
            System.out.println("______________________________");
                  
            } 
        } 
        
        
    } 
     
    public static void idealcalorie(double hig,String gen,double age,double wei) 
    { 
        double height=hig*2.25; 
        if(gen.equals("female")) 
        { 
            double ans=(10*wei)+(6.25*height)-(5*age)-161; 
            System.out.println("You need"+ans+"Calories/day to maintain your weight"); 
        } 
        if(gen.equals("male")) 
        { 
            double ans=(10*wei)+(6.25*height)-(5*age)+5; 
            System.out.println("You need"+ans+"Calories/day to maintain your weight"); 
        } 
        System.out.println("______________________________");
        
    } 
     
    public static void bodymassindex(double hig,double wei) 
    { 
        double height=hig*0.0254; 
        double ans=wei/(height*height); 
        System.out.println("your body mass index is "+ans); 
    } 
     
    public static void appointments() 
    { 
        System.out.println("Clinic will be open from 1pm to 8pm"); 
        System.out.println("with which doctor do you want yor appointment"); 
        System.out.println("______________________________");
        System.out.println("   press 1 for dr. ahmad"); 
        System.out.println("   press 2 for dr. ali"); 
        System.out.println("   press 3 for dr. rizwan"); 
        System.out.println("   press 4 for dr. Ahsan"); 
        System.out.println("______________________________");
        int cho=choice(); 
        switch (cho) { 
            case 1: 
                { 
                    int x=(int )(Math. random() * 8 + 1); 
                    System.out.println("your appointment with dr. ahmad is at "+x+"pm"); 
                    break; 
                } 
            case 2: 
                { 
                    int x=(int )(Math. random() * 8 + 1); 
                    System.out.println("your appointment with dr. ali is at "+x+"pm"); 
                    break; 
                } 
            case 3: 
                { 
                    int x=(int )(Math. random() * 8 + 1); 
                    System.out.println("your appointment with dr. rizwan is at "+x+"pm"); 
                    break; 
                }  
            case 4: 
                { 
                    int x=(int )(Math. random() * 8 + 1); 
                    System.out.println("your appointment with dr. Ahsan is at "+x+"pm"); 
                    break; 
                } 
            default: 
                break; 
        } 
        System.out.println("______________________________");
         
    } 
    public static void symptoms() 
    {
        System.out.println("____________________________________");
        System.out.println(" press 1 to check for malaria"); 
        System.out.println(" press 2 to check for cancer"); 
        System.out.println(" press 3 to check for Tuberculosis"); 
        System.out.println(" press 4 to check for diabetes"); 
        System.out.println("____________________________________");
        int cho=choice(); 
        switch (cho) { 
            case 1: 
                malaria(); 
                break; 
            case 2: 
                cancer(); 
                break; 
            case 3: 
                Tuberculosis(); 
                break; 
            case 4: 
                diabetes(); 
                break; 
            default: 
                break; 
        }
        System.out.println("______________________________");
         
    } 
    public static void malaria() 
    { 
        System.out.println("symptoms of malaria are following"); 
        System.out.println("Shaking chills that can range from moderate to severe"); 
        System.out.println("high fever"); 
        System.out.println("profuse sweating."); 
        System.out.println("headache."); 
        System.out.println("nausea."); 
         
    } 
    public static void cancer() 
    { 
        System.out.println("symptoms of cancer are following"); 
        System.out.println("Coughing, chest pain and breathlessness"); 
        System.out.println("Bleeding"); 
        System.out.println("Moles."); 
        System.out.println("Unexplained weight loss."); 
        System.out.println("Lump in your breast"); 
         
    } 
    public static void Tuberculosis() 
    { 
        System.out.println("symptoms of Tuberculosis are following"); 
        System.out.println("Coughing that lasts three or more weeks"); 
        System.out.println("Coughing up blood"); 
        System.out.println("pain with breathing"); 
        System.out.println("Fatigue"); 
        System.out.println("Fever"); 
         
    } 
    public static void diabetes() 
    { 
        System.out.println("symptoms of diabetes are following"); 
        System.out.println("Urinating often"); 
        System.out.println("Feeling very thirsty"); 
        System.out.println("Extreme fatigue"); 
        System.out.println("Blurry vision"); 
        System.out.println("Cuts/bruises that are slow to heal"); 
         
    } 
    public static void drdetails() 
    { 
        System.out.println("______________________________");
        System.out.println("(1) to check for dr. ahmad"); 
        System.out.println("(2) to check for dr. ali"); 
        System.out.println("(3) to check for dr. rizwan"); 
        System.out.println("(4) to check for dr. Ahsan");
        System.out.println("______________________________");
        int cho=choice(); 
        if (cho==1) 
        { 
            int age =40;  
            String specilist="social issues";  
            String education="PHD from Bahria university karachi";  
            String joiningdate="15 july 2012";  
            int officenumber=051625;  
            String residency ="Chak shehzad islamabad";  
            int  experience = 15; 
            System.out.println("Age of doctar is " + age  
            + "\n doctor is specialis in" + specilist   
            + "\n education of doctor is" + education  
            +"\n he has joined this hospital since "+ joiningdate  
            + "\n office number is " + officenumber  
            +"\n He is living in " + residency  
            + "\n his experience is more than" + experience  
            ); 
            
 
        } 
        if (cho==2) 
        { 
            int age =36;  
            int experience =11;  
            String specilist = " ENT Specilist "; 
            String education = "PHD from Liaquat institue of bio";  
            String joingdate= "10 dec. 2010";  
            String officenumber="051698745";  
            String livingin="Islamabad";  
            System.out.println("The doctor is " + age + "old"  
            +"\n he has an experience of " + experience + "years"  
            +"\n he has studied " + education   
            +"\n he has joined this hospital since " + joingdate  
            +"\n his office number " + officenumber  
            +"\n he is living in" + livingin  
            );  
 
        } 
        if (cho==3) 
        { 
            int age=28; 
            int experience =3;  
            String specilist = " cancer";  
            String education = "Bahria University";  
            String joingdate= "10 dec. 2012";  
            String officenumber="0516145";  
            String livingin="Islamabad"; 
            System.out.println("The doctor is " + age + "old"  
            +"\n he has an experience of " + experience + "years"  
            +"\n he has studied " + education   
            +"\n he has joined this hospital since " + joingdate  
            +"\n his office number " + officenumber  
            +"\n he is living in" + livingin  
            );  
 
        } 
        if (cho==4) 
        { 
            int age =33;  
       
            int experience =8;  
            String specilist = " bones ";  
            String education = "Bahria University";  
            String joingdate= "14-march. 2011";  
            String officenumber="0516145";  
            String livingin="Karachi";  
            System.out.println("The doctor is " + age + "old"  
            +"\n he has an experience of " + experience + "years"  
            +"\n he has studied " + education   
            +"\n he has joined this hospital since " + joingdate  
            +"\n his office number " + officenumber  
            +"\n he is living in" + livingin  
            );  
 
        } 
        System.out.println("______________________________");
    } 
    public static void medicines() 
    { 
        Scanner input=new Scanner(System.in); 
        String[] names={"calpol","panadol","klarisid","tandigyl","amryl","septron"}; 
        int[] cash={10,20,30,40,50,60}; 
        int total=0; 
        for(int i=0;i<6;i++) 
        { 
            System.out.println(names[i]); 
            
        } 
        System.out.println("are the names of the medicines available at the momment"); 
        System.out.println("______________________________");
        
        
        int a=1; 
        while(a==1) 
        { 
            System.out.println("Enter the name of the medicine you want to take "); 
            String chic=input.nextLine(); 
            for(int i=0;i<6;i++) 
            { 
                if(names[i].equals(chic)) 
                { 
                    total=total+cash[i]; 
                    System.out.println(names[i]+" is added to your cart "); 
                } 
            } 
        System.out.println("press 1 to buy another medicine "); 
        a=input.nextInt();
        input.nextLine();
        } 
        System.out.println("your total bill is "+total); 
        System.out.println("______________________________");
         
    }
     public static void Arraytofileconversion(String [][]data) 
    { 
        try{ 
            PrintWriter writer; 
            
            writer = new PrintWriter(pdata); 
            
            for(int i = 0; i<100 ; i++) 
            { 
                if(data[i][0] == null) 
                { 
                    break; 
                } 
                for(int j = 0 ; j<11 ; j++) 
                { 
                    writer.print(data[i][j] + "\t\t"); 
                } 
                
                writer.println(); 
            } 
            writer.close(); 
        } 
        catch(FileNotFoundException e) 
        { 
            System.out.println(e); 
        } 
        catch(Exception e) 
        { 
            System.out.println(e); 
        } 
    }
     public static void DataEntryFileToArray(String[][]data) 
    { 
        try 
        { 
            FileReader fr = new FileReader(pdata); 
            try (BufferedReader br = new BufferedReader(fr)) {
                String line;
                int i = 0;
                while (((line = br.readLine()) != null) && (i<100))
                {
                    
                    String[] splitted = line.split("\t\t");
                    for(int j = 0 ; j < 11 ; j++)
                    {
                        data[i][j] = splitted[j];
                    }
                    i++;
                }
            } 
        } 
        catch(IOException e) 
        { 
            System.out.println(e); 
        } 
    } 
} 
   

    
    
    

