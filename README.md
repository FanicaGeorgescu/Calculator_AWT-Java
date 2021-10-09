

import java.awt.*;
import java.awt.event.*;


public class CalculatorAWT{
    Frame f;
    double num1 =0;
    double num2 = 0;
    double result =0;



    CalculatorAWT (){
        f = new Frame("mini AWT calculator");
        Image icon = Toolkit.getDefaultToolkit().getImage("src/logo_calculator.png");
        f.setIconImage(icon);

        f.setSize(600,300);
        f.setLayout(new GridLayout(5, 0));

        Panel p1 = new Panel();
        p1.setLayout(new GridLayout());
        p1.setSize(100,50);
        Label  t1 = new Label(" enter first number");
        TextField text1  = new TextField();
        text1.setSize(100,50);
        p1.add(t1);
        p1.add(text1);
        p1.setVisible(true);

        Panel p2 = new Panel();
        p2.setLayout(new GridLayout());
        p2.setSize(100,50);
        Label  t2 = new Label(" choose operation");
        Choice operations = new Choice();
        operations.add("+");
        operations.add("-");
        operations.add("*");
        operations.add("/");
        p2.add(t2);
        p2.add(operations);
        p2.setVisible(true);

        Panel p3 = new Panel();
        p3.setLayout(new GridLayout());
        p3.setSize(100,50);
        Label  t3 = new Label(" enter second number");
        TextField text2  = new TextField();
        text2.setSize(100,50);
        p3.add(t3);
        p3.add(text2);
        p3.setVisible(true);
        Panel p4 = new Panel();
        p4.setLayout(new GridLayout());
        p4.setSize(100,400);
        Label  t4 = new Label(" ");
        Button calc  = new Button("calculate");
        calc.setSize(100,50);
        p4.add(t4);
        p4.add(calc);
        p4.setVisible(true);

        Panel p5 = new Panel();
        p5.setLayout(new GridLayout());
        p5.setSize(100,50);
        Label  t5 = new Label(" result is");
        TextField text3  = new TextField();
        text3.setSize(100,50);
        text3.setEditable(false);

        p5.add(t5);
        p5.add(text3);
        p5.setVisible(true);

        f.add(p1);
        f.add(p2);
        f.add(p3);
        f.add(p4);
        f.add(p5);

        f.setVisible(true);

        f.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });

        calc.addActionListener(new ActionListener(){
            public void actionPerformed(ActionEvent e){
                if(!text1.getText().equals("") && !text2.getText().equals("")){
                    int flag=0;
                    double result=0.0;
                    double firstNumber=0.0,secondNumber=0.0;
                    try{
                        firstNumber=Double.parseDouble(text1.getText());
                        secondNumber=Double.parseDouble(text2.getText());
                        String operator=operations.getSelectedItem();



                        if(operator.equals("+")){
                            result=firstNumber+secondNumber;
                        }
                        else if(operator.equals("-")){
                            result=firstNumber-secondNumber;
                        }
                        else if(operator.equals("*")){
                            result=firstNumber*secondNumber;
                        }


                        else if(operator.equals("/")){
                            if(secondNumber==0){
                                flag=1;
                            }
                            else{
                                result=firstNumber/secondNumber;
                            }

                        }
                    }
                    catch(Exception ec){
                        flag=2;
                    }






                    if(flag==1){
                        text3.setText("Please second number not 0");
                    }
                    else if(flag==2){
                        text3.setText("Please numbers must be integers");
                    }
                    else{
                        text3.setText(String.valueOf(result));
                    }

                }
                else{
                    text3.setText("Please must enter both values");
                }







            }
        });
    }
    public static void main(String[] args){

        CalculatorAWT calc = new CalculatorAWT();



    }


}
