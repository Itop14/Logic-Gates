# Logic-Gates C#

This program will give the students the answer to logic gate questions
For example:
Enter logic gate : OR
Enter first input : 1
Enter second input : 0
Result = 1
It should work for the logic gates OR, AND, XOR, NAND and NOR

    using System;
    using System.Collections.Generic;
    using System.ComponentModel;
    using System.Data;
    using System.Drawing;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows.Forms;
    
    namespace Logic_gate
    {
        public partial class Form1 : Form
        {
            public Form1()
            {
                InitializeComponent();
            }
    
            private void answer_btn_Click(object sender, EventArgs e)
            {
                int result = 0;
                
                int input1 = radioButton1.Checked ? 1 : 0;// See if the user picked 1 or 0
                int input2 = radioButton3.Checked ? 1 : 0;// See if the user picked 1 or 0
                
                string gateType = Logic_gates.SelectedItem != null ? Logic_gates.SelectedItem.ToString() : string.Empty; // See what logic gate the user picked
                if (string.IsNullOrEmpty(gateType))// In case the user hasnt picked any logic gate
                {
                    MessageBox.Show("Please select a logic gate.");
                    return;
                }
    
                switch (gateType)
                {
                    case "OR":
                        result = input1 | input2;
                        break;
                    case "AND":
                        result = input1 & input2;
                        break;
                    case "XOR":
                        result = input1 ^ input2;
                        break;
                    case "NAND":
                        result = input1 & input2;
                        result = result == 1 ? 0 : 1; //Just the inverse of AND
                        break;
                    case "NOR":
                        result = input1 | input2;
                        result = result == 1 ? 0 : 1; //Just the inverse of OR
                        break;
                    default:
                        return;
                }
    
                result_lab.Text = "Result = " + result;
            }
            
        }
    }
