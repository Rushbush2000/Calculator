import java.awt.*;
import java.awt.event.*;

public class Calculator extends Frame implements ActionListener {
    TextField tfNum1, tfNum2, tfResult;
    Button btnAdd, btnSubtract, btnMultiply, btnDivide;

    public Calculator() {
        
        tfNum1 = new TextField();
        tfNum1.setBounds(150, 50, 150, 20);

        tfNum2 = new TextField();
        tfNum2.setBounds(150, 100, 150, 20);

        tfResult = new TextField();
        tfResult.setBounds(150, 200, 150, 20);
        tfResult.setEditable(false);  

       
        Label lblNum1 = new Label("Number 1:");
        lblNum1.setBounds(50, 50, 80, 20);

        Label lblNum2 = new Label("Number 2:");
        lblNum2.setBounds(50, 100, 80, 20);

        Label lblResult = new Label("Result:");
        lblResult.setBounds(50, 200, 80, 20);

        
        btnAdd = new Button("Add");
        btnAdd.setBounds(50, 150, 80, 30);
        btnAdd.addActionListener(this);

        btnSubtract = new Button("Subtract");
        btnSubtract.setBounds(140, 150, 80, 30);
        btnSubtract.addActionListener(this);

        btnMultiply = new Button("Multiply");
        btnMultiply.setBounds(230, 150, 80, 30);
        btnMultiply.addActionListener(this);

        btnDivide = new Button("Divide");
        btnDivide.setBounds(320, 150, 80, 30);
        btnDivide.addActionListener(this);

        
        add(lblNum1);
        add(lblNum2);
        add(lblResult);
        add(tfNum1);
        add(tfNum2);
        add(tfResult);
        add(btnAdd);
        add(btnSubtract);
        add(btnMultiply);
        add(btnDivide);

        
        setSize(450, 300);
        setLayout(null); 
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            
            double num1 = Double.parseDouble(tfNum1.getText());
            double num2 = Double.parseDouble(tfNum2.getText());
            double result = 0;

            
            if (e.getSource() == btnAdd) {
                result = num1 + num2;
            } else if (e.getSource() == btnSubtract) {
                result = num1 - num2;
            } else if (e.getSource() == btnMultiply) {
                result = num1 * num2;
            } else if (e.getSource() == btnDivide) {
                if (num2 == 0) {
                    tfResult.setText("Error: Divide by 0");
                    return;
                }
                result = num1 / num2;
            }

            
            tfResult.setText(String.valueOf(result));

        } catch (NumberFormatException ex) {
            tfResult.setText("Invalid Input");
        }
    }

    public static void main(String[] args) {
        new Calculator();  
    }
}
