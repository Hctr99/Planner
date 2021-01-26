package Clases_GUIs;
import java.awt.LayoutManager;
import java.awt.event.*;
import javax.swing.*;

import Manejo_Archivos.GestorVentanas;
import Manejo_Archivos.GestorArchivos;

public class Ventana_metas_completadas extends JFrame implements ActionListener{
    private JLabel etiqueta1;
    private JButton boton1;
    private JTextArea listaMetas;
    private JScrollPane scroll;
    private GestorVentanas gestorVentanas;
    private GestorArchivos gestorArchivos;

    public Ventana_metas_completadas(){
        //layout
        setLayout(null);
        //etiqueta
        this.etiqueta1 = new JLabel("Metas Completadas");
        this.etiqueta1.setBounds(80, 10, 500, 30);
        this.add(this.etiqueta1);
        //botones
        this.boton1 = new JButton("Atras");
        this.boton1.setBounds(230, 10, 100, 30);
        this.add(this.boton1);
        this.boton1.addActionListener(this);
        //texto 
        this.listaMetas = new JTextArea("");
        this.listaMetas.setEditable(false);
        //scroll
        this.scroll= new JScrollPane(listaMetas);
        this.scroll.setBounds(10,60,365,420);
        this.scroll.setFont(new java.awt.Font("Tahoma", 0,14));
        this.add(scroll);
        this.gestorVentanas = new GestorVentanas();
        this.gestorArchivos = new GestorArchivos();
        this.listaMetas=gestorArchivos.escribirTexto("MetasCompletadas",this.listaMetas);
    }

    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == this.boton1) {
            this.gestorVentanas.ejecutarVentanaMenu();
            this.setVisible(false);
        }

    }


    
}
