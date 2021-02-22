# Averiguar area y volumen en funcion de una diagonal
## Indice
  - Codigo fuente
  - Creador 😎
### Codigo fuente
Pues aqui ta otra vez :v
Esta vez he usado la programacion orientada a objetos solo por variar un poco

Controladores de la ventana: 
```CSHARP
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Don_t_worry__be_happy
{
    public partial class Form1 : Form
    {
        Cubo cSalida = new Cubo();
        int x = 1;
        public Form1()
        {
            InitializeComponent();
            Area.ReadOnly = true;
            Volumen.ReadOnly = true;
            richTextBox1.ReadOnly = true;
            label4.Visible = false;
        }

        private void Entrada_TextChanged(object sender, EventArgs e)
        {
            if (Entrada.Text == "")
            {
                Area.Text = "";
                Volumen.Text = "";
                
                return;
            }
            try
            {
                double dEnt = Double.Parse(Entrada.Text);
                cSalida.Lado = dEnt;
                string[] sArrayOfElements = { "Area", "Volumen" };
                Area.Text = $"{cSalida.calculateFromDiagonal(dDiagonal: cSalida.Lado, sResult: sArrayOfElements[0])}";
                Volumen.Text = $"{cSalida.calculateFromDiagonal(dDiagonal: cSalida.Lado, sResult: sArrayOfElements[1])}";
                
            }
            catch (FormatException)
            {
                label4.Visible = true;
                timer1.Start();
            }
        }

        private void Entrada_KeyDown(object sender, KeyEventArgs e)
        {
            if(e.KeyCode == Keys.Enter)
            {
                try
                {
                    double dEnt = Double.Parse(Entrada.Text);
                    richTextBox1.AppendText($"\nCalculo {x}: \n" +
                                        $"  Entrada:{Entrada.Text}\n" +
                                        $"  Salida: \n    Area => {Area.Text}\n    Volumen => {Volumen.Text}");
                    x++;
                }
                catch (FormatException)
                {

                }
            }
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            label4.Visible = false;
        }

        private void button1_Click(object sender, EventArgs e)
        {
            System.Diagnostics.Process.Start("");
        }
    }
}
```

Clase del cubo (No soy muy original):
```CSHARP
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms.DataVisualization.Charting;

namespace Don_t_worry__be_happy
{
    class Cubo
    {
        // Usando buenas practicas de programador indicando el tipo de dato con la letra inicial del tipo xd
        public double Lado { get; set;}
        // Retorna, dependiendo del argumento de entrada, el area o volumen
        public double calculateFromDiagonal(double dDiagonal = 8472873623786578478.47268372877482348728, string sResult = "uh uihwduhhu hwhdjihwah jhwjhdj hjwkhdjahdkj h")
        {
            ArgumentException eArg = new ArgumentException($"Debes introducir un tipo de valor a retornar\n" +
                                            $"Resultado introducido        ->{sResult}\n" +
                                            $"Resultado esperado           -> Area || Volumen", sResult);
            if (dDiagonal == 8472873623786578478.47268372877482348728 || sResult == "uh uihwduhhu hwhdjihwah jhwjhdj hjwkhdjahdkj h")
                throw eArg;
            double dSemiR = Math.Sqrt(Math.Pow(dDiagonal / 2, 2) + Math.Pow(dDiagonal / 2, 2));
            switch (sResult)
            {
                case "Area":
                    return Math.Pow(6 * dSemiR, 2);
                case "Volumen":
                    return Math.Pow(dSemiR, 3);
                default:
                    throw eArg;
            }
        }
    }
}
```

### Creador
Pues el unico full-stack developer de la clase xd
