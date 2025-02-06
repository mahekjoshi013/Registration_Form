package Package_ABC;
import javax.swing.*;
import java.util.*;
import java.awt.event.*;
public class Registration_Form
{
	String n,l,e,no;
	Scanner sc = new Scanner(System.in);
	Boolean b;
	JFrame fm;
	JLabel jl, name,last,email,phone,con, pl,plc,gender;
	JTextField name_i, last_i,email_i,phone_i;
	JPasswordField pl_i, plc_i;
	JRadioButton male, female, other;
	ButtonGroup gender_bg;
	JCheckBox checkbox;
	JButton submit, preview,reset;
	JDialog previewbox,submitbox;
	JComboBox<String> combobox;
	
	public void Input()
	{
		System.out.println("Please Enter your First Name: ");
		n = sc.next();
		if((Character.isUpperCase(n.charAt(0))) != true)
		{
			while((Character.isUpperCase(n.charAt(0))) == false)
			{
				System.out.println("Please Enter the first letter of the name in UpperCase!!");
				n = sc.next();
			}
		}
		
		System.out.println("\nPlease Enter your Last Name: ");
		l = sc.next();
		if((Character.isUpperCase(l.charAt(0))) != true)
		{
			while((Character.isUpperCase(l.charAt(0))) == false)
			{
				System.out.println("Please Enter the first letter of the Surname in UpperCase!!");
				l = sc.next();
			}
		}
		
		String el;
        String invalidChars = "!#$%^&*()=+{}[]|;:'\",<>?/"; // Invalid special characters
        System.out.print("\nEnter your Email Address:\n");
        el = sc.next();
        if (isValidEmail(el, invalidChars) == false)
        { 
        	System.out.println("Invalid Email. Please Enter Again!!");
        	el = sc.next();
        while (true)
            {  // Keep asking until a valid email is entered
            if (isValidEmail(el, invalidChars) == true)
            {  
                break;  // Exit the loop when email is valid
            } 
        }
        }
        System.out.println("\nPlease enter your Phone Number: ");
        no = sc.next();
        if((no.charAt(0) != '9' || no.charAt(0) != '8' || no.charAt(0) != '7' || no.charAt(0) != '6') || (no.length() != 10))
		{
			while((no.charAt(0) != '9' && no.charAt(0) != '8' && no.charAt(0) != '7' && no.charAt(0) != '6') || (no.length() != 10))
			{
				System.out.println("Invalid Phone Number!! Please Enter again: ");
				no = sc.next();
			}
		}
		e = el;		
	}
	
	public static boolean isValidEmail(String email, String invalidChars)
{
        if (!email.endsWith("@gmail.com"))
        { // Check if it ends with @gmail.com
            return false;
        }

        int atIndex = email.indexOf("@gmail.com"); // Position of '@gmail.com'
        if (atIndex == 0)
        {  // Ensure there's at least one character before '@'
            return false;
        }
        
        if(!Character.isLowerCase(email.charAt(0)))
        {
        	return false;
        }

        // Check for invalid special characters
        for (int i = 0; i < atIndex; i++)
        {
            char ch = email.charAt(i);
            if (invalidChars.indexOf(ch) != -1)
            {
                return false;
            }
        }

        return true;  // If all conditions are met, return true
    }
			
	public void Frames()
	{
		fm = new JFrame("Sign-Up Form");
		
		submit = new JButton("Submit");
		submit.setBounds(35, 650, 100, 25);
		
		preview = new JButton("Preview");
		preview.setBounds(150, 650, 100, 25);
		
		reset = new JButton("Reset");
		reset.setBounds(265, 650, 100, 25);
	}
	
	public void Labels()
	{
		//Form Heading
		jl = new JLabel("PLEASE ENTER YOUR INFORMATION:");
		jl.setBounds(215,35,250,25);	
		
		//Label Name
		name = new JLabel("Please Enter your First Name:");
		name.setBounds(50, 125, 200, 25);
		
		//Label Surname
		last = new JLabel("Please Enter your Last Name:");
		last.setBounds(50, 175, 200, 25);
				
		//Label email
		email = new JLabel("Please Enter your Email:");
		email.setBounds(50, 225, 200, 25);
		
		//label phone number
		phone = new JLabel("Please Enter your Phone Number:");
		phone.setBounds(50, 275, 200, 25);
		
		//label country
		con = new JLabel("Please enter your Country: ");
		con.setBounds(50, 325, 200, 25);
		
		//label password
		pl = new JLabel("Please enter your Password:");
		pl.setBounds(50,375,200,25);
		
		//label confirm password
		plc = new JLabel("Please confirm your Password:");
		plc.setBounds(50,405,200,25);
		
		//label gender
		gender = new JLabel("Please enter your Gender: ");
		gender.setBounds(50, 475, 200, 25);
		
		
		checkbox = new JCheckBox("I Agree to the Terms & Conditions");
		checkbox.setBounds(30, 600, 300, 25);
		
	}
		
	public void TextFields()
	{
		name_i = new JTextField(n);
		name_i.setBounds(300, 125, 200, 25);
		
		last_i = new JTextField(l);
		last_i.setBounds(300, 175, 200, 25);
		
		email_i = new JTextField(e);
		email_i.setBounds(300, 225, 200, 25);
		
		phone_i = new JTextField(no);
		phone_i.setBounds(300, 275, 200, 25);
		
		pl_i = new JPasswordField();
		pl_i.setBounds(300, 375, 200, 25);
		
		plc_i = new JPasswordField();
		plc_i.setBounds(300, 405, 200, 25);	
	}
		
	public void RadioBtn()
	{
	    gender_bg = new ButtonGroup();
	    
	    male = new JRadioButton("Male");
	    male.setBounds(285, 475, 80, 25);  // Reduced width
	    gender_bg.add(male);
	    fm.add(male);
		
	    female = new JRadioButton("Female");
	    female.setBounds(375, 475, 80, 25);  // Adjusted position
	    gender_bg.add(female);
	    fm.add(female);	    
	    
	    other = new JRadioButton("Other");
	    other.setBounds(480, 475, 80, 25);  // Adjusted position
	    gender_bg.add(other);
		fm.add(other);
	}
		
	public void ComboBox()
	{
		
		String[] Countries = {"India", "Afghanistan", "Pakistan", "China", "Nepal", "Bhutan", "Sri Lanka"};
		combobox = new JComboBox<>(Countries);
		combobox.setBounds(300, 325, 200, 25);
	}	
	
	public void addSubmitActionListener()
	{
        submit.addActionListener(new ActionListener()
        {
            public void actionPerformed(ActionEvent ae)
            {
            	submitbox = new JDialog();
            	JLabel sub = new JLabel("Your Information is submitted Successfully!");
                sub.setBounds(50,150,300,25);
                submitbox.add(sub);
                submitbox.setSize(400,400);
        		submitbox.setLayout(null);
        		submitbox.setVisible(true);
            }
            
        });
    }	
	
	public void addPreviewActionListener()
	{
        preview.addActionListener(new ActionListener()
        {
            public void actionPerformed(ActionEvent ae)
            {
            	previewbox = new JDialog();
            	           	
                JLabel name_p = new JLabel("First Name:  ");
                JLabel namep = new JLabel(name_i.getText());
                name_p.setBounds(50,65,300,25);
                namep.setBounds(175,65,300,25);
                previewbox.add(name_p);
                previewbox.add(namep);
                
                JLabel last_p = new JLabel("Last Name:  ");
                JLabel lastp = new JLabel(last_i.getText());
                last_p.setBounds(50,95,300,25);
                lastp.setBounds(175,95,300,25);
                previewbox.add(last_p);
                previewbox.add(lastp);
                
                JLabel email_p = new JLabel("E-mail:  ");                               
                JLabel emailp = new JLabel(email_i.getText());
                email_p.setBounds(50,125,300,25);
                emailp.setBounds(175,125,300,25);
                previewbox.add(email_p);
                previewbox.add(emailp);
                               
                JLabel phone_p = new JLabel("Phone Number:  ");
                JLabel phonep = new JLabel(phone_i.getText());
                phone_p.setBounds(50,155,300,25);
                phonep.setBounds(175,155,300,25);
                previewbox.add(phone_p);
                previewbox.add(phonep);
                
                JLabel gender = new JLabel("Gender: ");
                gender.setBounds(50,185,300,25);
            	previewbox.add(gender);
                if (male.isSelected())
                {
                	JLabel male_p = new JLabel("Male");
                	male_p.setBounds(175,185,300,25);
                	previewbox.add(male_p);
                }
                else if (female.isSelected())
                {
                	JLabel female_p = new JLabel("Female");
                	female_p.setBounds(175,185,300,25);
                	previewbox.add(female_p);
                }
                else if(other.isSelected())
                {
                	JLabel other_p = new JLabel("Other");
                	other_p.setBounds(175,185,300,25);
                	previewbox.add(other_p);
                }

                JLabel con_p = new JLabel("Country:  ");               
                JLabel conp = new JLabel((String) combobox.getSelectedItem());
                con_p.setBounds(50,215,100,25);
                conp.setBounds(175,215,100,25);
                previewbox.add(con_p);
                previewbox.add(conp);
                
                previewbox.setSize(400,400);
        		previewbox.setLayout(null);
        		previewbox.setVisible(true);
            }
            
        });
    }
    
    public void addResetActionListener()
	{
        reset.addActionListener(new ActionListener()
        {
            public void actionPerformed(ActionEvent ae)
            {
            	name_i.setText("");
            	last_i.setText("");
            	email_i.setText("");
            	phone_i.setText("");
            	combobox.setSelectedItem(null);
            	pl_i.setText("");
            	plc_i.setText("");
            	gender_bg.clearSelection();
            	checkbox.setSelected(false);
            }
            
        });
    }

	public void Add()
	{
		fm.add(jl);
		fm.add(name);
		fm.add(name_i);
		fm.add(last);
		fm.add(last_i);
		fm.add(email);
		fm.add(email_i);
		fm.add(phone);	
		fm.add(phone_i);
		fm.add(con);
		fm.add(combobox);		
		fm.add(pl);
		fm.add(plc);
		fm.add(pl_i);
		fm.add(plc_i);
		fm.add(gender);		
		fm.add(checkbox);
		fm.add(submit);
		fm.add(preview);
		fm.add(reset);
		
		addSubmitActionListener();
		addPreviewActionListener();
		addResetActionListener();
		
		fm.setSize(700,1000);
		fm.setLayout(null);
		fm.setVisible(true);
		
	}
			
	public static void main(String args[])
	{
		// TODO Auto-generated method stub
		Registration_Form ob = new Registration_Form();
		ob.Input();
		ob.Frames();
		ob.Labels();
		ob.TextFields();
		ob.ComboBox();
		ob.RadioBtn();
		//ob.addPreviewActionListener();
		ob.Add();
		ob.sc.close();
	}
}
