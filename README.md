# TopicosWeb
Sitio web para la  creación de programas en la clase Tópicos Avanzados de Programacion
package tarea3;

import java.awt.*;
import java.awt.event.*;

import javax.swing.*;
import javax.swing.event.*;

public class DemoMiSelectorDeColor extends JFrame {

    private MiSelectorDeColor selector;

    public DemoMiSelectorDeColor() {
        super("-------MI SELECTOR DE COLOR-------"); // se crea el cuadro
        String demo = "ESTE ES EL EJERCICIO SELECTOR DE COLOR"
                + "EN DONDE : Declare a una subclase de JPanel llamada"
                + " MiSelectorDeColor , que proporcione tres objetos JSlider"
                + " y tres objetos JTextField. \n "
                + "TRABAJO PRESENTADO POR :  \n"
                + "MAYRA MONSERRAT GASPAR VENEGAS   \n"
                + "AMADO RAMOS ZUÑIGA \n"
                + "----- TERRONES---";

        Container Contenedor = getContentPane(); // obtiene el panel de contenido
        Contenedor.setLayout(new BorderLayout());

        selector = new MiSelectorDeColor();
        this.add(selector, BorderLayout.NORTH);

        setSize(500, 300);// establece el tamaño del marco
        setVisible(true); // muestra el marco
    }

    public static void main(String args[]) {
        DemoMiSelectorDeColor test = new DemoMiSelectorDeColor();
        test.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    }
}
------------------------------------

package tarea3;

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.event.*;

public class MiSelectorDeColor extends JPanel {
    

    private JSlider sliderrojo, sliderverde, sliderazul;
    private JTextField camporojo, campoverde, campoazul, camposalida;// el texto resaltado se copia aquí
    private JPanel panelrojo, panelverde, panelazul, panelcontroles, panelresultados, 
            paneldescripcion, panelfinal;
    private JLabel salidaetiqueta, etiqueta1, etiqueta2, etiqueta3;
    private int rojo, verde, azul;
    private Color CRojo, CVerde, CAzul, CFinal; // colores

    public MiSelectorDeColor() {
        
        panelrojo = new JPanel();
        // alineacion del panel rojo
        panelrojo.setLayout(new FlowLayout());

        panelverde = new JPanel();
         // alineacion del panel verde
        panelverde.setLayout(new FlowLayout());

        panelazul = new JPanel();
        // alineacion del panel azul
        panelazul.setLayout(new FlowLayout());

        panelcontroles = new JPanel();
        panelcontroles.setLayout(new GridLayout(3, 1)); // 3 por 1 sin espacios

        panelresultados = new JPanel();
        panelresultados.setLayout(new FlowLayout());

        paneldescripcion = new JPanel();
        paneldescripcion.setLayout(new GridLayout(1, 3));// 1 por 3 sin espacios

        panelfinal = new JPanel();
        panelfinal.setLayout(new BorderLayout());

        //representa los valores de 0 a 255 para las partes de color rojo
        sliderrojo = new JSlider(SwingConstants.HORIZONTAL, 0, 255, 1);
        sliderrojo.setMajorTickSpacing(10);
        sliderrojo.setPaintTicks(true);

            // Use usan estos valores como argumentos para el constructor de Color,
        //para crear un nuevo objeto Color rojo.
        sliderrojo.addChangeListener(
                new ChangeListener() {

                    public void stateChanged(ChangeEvent e) {
                        rojo = sliderrojo.getValue();
                        CRojo = new Color(rojo, 0, 0);
                        camporojo.setBackground(CRojo);
                        repaint();

                    }
                }
        );

        camporojo = new JTextField(1);
        camporojo.setEditable(false);

        panelrojo.add(sliderrojo);
        panelrojo.add(camporojo);
 
        ////representa los valores de 0 a 255 para las partes de color verde
        sliderverde = new JSlider(SwingConstants.HORIZONTAL, 0, 255, 1);
        sliderverde.setMajorTickSpacing(10);
        sliderverde.setPaintTicks(true);

             // Use usan estos valores como argumentos para el constructor de Color,
        //para crear un nuevo objeto Color verde.
        sliderverde.addChangeListener(
                new ChangeListener() {

                    public void stateChanged(ChangeEvent e) {
                        verde = sliderverde.getValue();
                        CVerde = new Color(0, verde, 0);
                        campoverde.setBackground(CVerde);
                        repaint();

                    }
                }
        );

        campoverde = new JTextField(1);
        campoverde.setEditable(false);

        panelverde.add(sliderverde);
        panelverde.add(campoverde);

        ////representa los valores de 0 a 255 para las partes de color azul
        sliderazul = new JSlider(SwingConstants.HORIZONTAL, 0, 255, 1);
        sliderazul.setMajorTickSpacing(10);
        sliderazul.setPaintTicks(true);

         // Use usan estos valores como argumentos para el constructor de Color,
        //para crear un nuevo objeto Color azul.
        sliderazul.addChangeListener(
                new ChangeListener() {

                    public void stateChanged(ChangeEvent e) {
                        azul = sliderazul.getValue();
                        CAzul = new Color(0, 0, azul);
                        campoazul.setBackground(CAzul);
                        repaint();
                    }
                }
        );

        campoazul = new JTextField(1);
        campoazul.setEditable(false);

        panelazul.add(sliderazul);
        panelazul.add(campoazul);

        camposalida = new JTextField(5); 
        camposalida.setEditable(false); 

        salidaetiqueta = new JLabel("Resultado");  //  CAMPO DE TEXTO RESULTADO 

        etiqueta1 = new JLabel("Slider1");// CAMPO DE TEXTO SLIDER 1
        etiqueta1.setFont(new Font("Arial", Font.BOLD, 12));// SE CONFIGURA EL TAMAÑO Y TIPO DE LETRA
        etiqueta1.setForeground(Color.RED); // SE CONFIGURA EL COLOR DEL TEXTO

        etiqueta2 = new JLabel("Slider2");// CAMPO DE TEXTO SLIDER 2
        etiqueta2.setFont(new Font("Arial", Font.BOLD, 12));// SE CONFIGURA EL TAMAÑO Y TIPO DE LETRA
        etiqueta2.setForeground(Color.GREEN); // SE CONFIGURA EL COLOR DEL TEXTO

        etiqueta3 = new JLabel("Slider3"); // CAMPO DE TEXTO SLIDER 3
        etiqueta3.setFont(new Font("Arial", Font.BOLD, 12)); // SE CONFIGURA EL TAMAÑO Y TIPO DE LETRA
        etiqueta3.setForeground(Color.BLUE); // SE CONFIGURA EL COLOR DEL TEXTO

        panelresultados.add(salidaetiqueta);// AGREGA LA ETIQUETA DE SALIDA O RESULTADO AL PANEL
        panelresultados.add(camposalida); // AGREGA EL PANEL DE SALIDA O RESULTADO

        panelcontroles.add(panelrojo);// AGREGA EL PANEL ROJO DE CONTROL 
        panelcontroles.add(panelverde);// AGREGA EL PANEL VERDE DE CONTROL 
        panelcontroles.add(panelazul); // AGREGA EL PANEL AZUL DE CONTROL 

        paneldescripcion.add(etiqueta1);// AGREGA LA ETIQUETA 1 DE LA DESCRIPCION  AL PANEL
        paneldescripcion.add(etiqueta2);// AGREGA LA ETIQUETA 2 DE LA DESCRIPCION  AL PANEL
        paneldescripcion.add(etiqueta3); // AGREGA LA ETIQUETA 3  DE LA DESCRIPCION AL PANEL

        panelfinal.add(panelcontroles, BorderLayout.NORTH); // AGREGA EL PANEL DE CONTROLES
        panelfinal.add(panelresultados, BorderLayout.CENTER);
        panelfinal.add(paneldescripcion, BorderLayout.SOUTH);


        add(panelfinal); // AGREGA EL PANEL FINAL 

    }

    public void paintComponent(Graphics g) {
        super.paintComponent(g);
        CFinal = new Color(rojo, verde, azul);
        camposalida.setBackground(CFinal);
        //  imprime los Slider de cada color
        etiqueta1.setText("Valor Slider1: " + sliderrojo.getValue());
        etiqueta2.setText("    Valor Slider2: " + sliderverde.getValue());
        etiqueta3.setText("           Valor Slider3: " + sliderazul.getValue());
    }
}

