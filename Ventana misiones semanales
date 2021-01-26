package Clases_GUIs;
import javax.swing.*;
import java.awt.event.*;
import java.awt.Component;
import java.awt.LayoutManager;
import java.util.*;

import Manejo_Archivos.GestorVentanas;
import Manejo_Archivos.GestorArchivos;

public class Ventana_misiones_semanales extends JFrame implements ItemListener,ActionListener {

    private JComboBox combo1;
    private JButton boton1,boton2,boton3,boton4;
    private JLabel etiqueta1,etiqueta2, etiqueta3,etiqueta4;
    private GestorVentanas gestorVentanas;
    private String dia;
    private JScrollPane scroll;
    private JTextArea listaMisiones;
    private GestorArchivos gestorArchivos;
    private JTextField numeroEliminar;
    private int num;

    public Ventana_misiones_semanales() {
        //textField
        numeroEliminar=new JTextField();
        numeroEliminar.setBounds (245, 105, 34, 20);
        add(numeroEliminar);
        //layout
        this.setLayout(null);
        //etiquetas
        this.etiqueta1 = new JLabel("Seleccionar Día:");
        this.etiqueta1.setBounds(10, 10, 200, 30);
        this.add(this.etiqueta1);
        this.etiqueta2 = new JLabel("Lista de Misiones:");
        this.etiqueta2.setBounds(10, 100, 200, 30);
        this.add(this.etiqueta2);
        this.etiqueta3 = new JLabel("Si quiere eliminar una misión");
        this.etiqueta3.setBounds(130, 80, 200, 30);
        this.add(this.etiqueta3);
        this.etiqueta4 = new JLabel("ingrese su numero:");
        this.etiqueta4.setBounds(130, 100, 200, 30);
        this.add(this.etiqueta4);
        //combo
        this.combo1 = new JComboBox();
        this.combo1.setBounds(120,10,80,30);
        this.add(combo1);
        this.combo1.addItem("");
        this.combo1.addItem("Lunes");
        this.combo1.addItem("Martes");
        this.combo1.addItem("Miercoles");
        this.combo1.addItem("Jueves");
        this.combo1.addItem("Viernes");
        this.combo1.addItem("Sabado");
        this.combo1.addItem("Domingo");
        this.combo1.addItemListener(this);
        //botones
        this.boton1 = new JButton("Nueva Misión");
        this.boton1.setBounds(10, 50, 150, 30);
        this.add(this.boton1);
        this.boton1.addActionListener(this);
        this.boton2 = new JButton("Atras");
        this.boton2.setBounds(230, 10, 100, 30);
        this.add(this.boton2);
        this.boton2.addActionListener(this);
        this.boton3 = new JButton("Eliminar misiones del Día");
        this.boton3.setBounds(170, 50, 200, 30);
        this.add(this.boton3);
        this.boton3.addActionListener(this);
        this.boton4 = new JButton("Eliminar");
        this.boton4.setBounds(285, 105, 90, 20);
        this.add(this.boton4);
        this.boton4.addActionListener(this);
        //texto 
        this.listaMisiones = new JTextArea("");
        this.listaMisiones.setEditable(false);
        //scroll
        this.scroll= new JScrollPane(listaMisiones);
        this.scroll.setBounds(10,130,365,350);
        this.scroll.setFont(new java.awt.Font("Tahoma", 0,14));
        this.add(scroll);
        //
        this.dia="";
        this.gestorVentanas= new GestorVentanas();
        this.gestorArchivos=new GestorArchivos();

    }

    public void itemStateChanged(ItemEvent e) {
        if (e.getSource() == combo1) {
            this.dia = combo1.getSelectedItem().toString();
        }
        this.listaMisiones=gestorArchivos.escribirTexto("Mision"+this.dia,this.listaMisiones);

    }

    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == this.boton1) {
            this.gestorVentanas.ejecutarVentanaAgregarMisiones();
            this.setVisible(false);

        }
        if (e.getSource() == this.boton2) {

            this.gestorVentanas.ejecutarVentanaMenu();
            this.setVisible(false);
        }
        if (e.getSource() == this.boton3) {

            this.listaMisiones=gestorArchivos.escribirTexto("Mision"+this.dia,this.listaMisiones);

            if (JOptionPane.showConfirmDialog(null, "Estás seguro?")==0) {
                this.gestorArchivos.eliminarArchivos("Mision"+this.dia);
                JOptionPane.showConfirmDialog(null, "Misiones del dia: " + this.dia + " eliminadas correctamente", "Exito!!!", JOptionPane.DEFAULT_OPTION);
                this.listaMisiones.setText("");
            }
        }

        if (e.getSource()==this.boton4){ //eliminar
            if(this.dia!=""&&this.dia!=null){

                if (validacionSoloNumeros(numeroEliminar.getText())==true){
                    if(this.num>(this.gestorArchivos.contarLineas("Mision"+this.dia)-1)||this.num<1){
                        JOptionPane.showConfirmDialog(null,"Verifique los datos","ERROR", JOptionPane.DEFAULT_OPTION,JOptionPane.ERROR_MESSAGE);

                    }else{
                        if (JOptionPane.showConfirmDialog(null, "Estás seguro?")==0){

                            this.gestorArchivos.guardarArchivo("Mision"+dia,gestorArchivos.borrarLinea(this.num,"Mision"+this.dia));//borra
                            this.listaMisiones=gestorArchivos.escribirTexto("Mision"+this.dia,this.listaMisiones);//actualiza
                            ArrayList<String> viejos = new ArrayList<String>();
                            ArrayList<String> sinNumero = new ArrayList<String>();
                            ArrayList<String> actualizados = new ArrayList<String>();
                            int hastaCuando=this.gestorArchivos.contarLineas("Mision"+this.dia);

                            for(int i=1;i<hastaCuando;i++){
                                viejos.add(this.gestorArchivos.leerUnaLinea("Mision"+this.dia,i));//agrega los actuales sin editar


                            }
                            this.gestorArchivos.eliminarArchivos("Mision"+this.dia);
                            this.gestorArchivos.crearArchivo("Mision"+this.dia);
                            for(int i=1;i<hastaCuando;i++){
                                sinNumero.add(this.gestorArchivos.quitarNumero(viejos.get(i-1)));//agrega los sin numero

                                actualizados.add(i+"| "+sinNumero.get(i-1));//agrega los preparados

                                this.gestorArchivos.agregarTexto("Mision"+this.dia,actualizados.get(i-1));//los escribe


                            }
                            this.listaMisiones=gestorArchivos.escribirTexto("Mision"+this.dia,this.listaMisiones);//actualiza
                            viejos.clear();
                            sinNumero.clear();
                            actualizados.clear();
                            
                            

                            

                        }

                    }
                }else{
                    JOptionPane.showConfirmDialog(null,"Verifique los datos","ERROR", JOptionPane.DEFAULT_OPTION,JOptionPane.ERROR_MESSAGE);
                    //ok=0

                }
            }else {
                JOptionPane.showConfirmDialog(null,"Verifique los datos","ERROR", JOptionPane.DEFAULT_OPTION,JOptionPane.ERROR_MESSAGE);
            }
            //ok=0

        }
    }

    public boolean validacionSoloNumeros(String cadena){

        try{
            this.num=Integer.parseInt(cadena);
            return true;

        }
        catch (Exception e)
        {

            return false;
        }

    }
}

