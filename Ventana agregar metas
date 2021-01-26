package Clases_GUIs;
import java.awt.LayoutManager;
import java.awt.event.*;
import javax.swing.*;
import Clases_Dominio.Metas;
import Manejo_Archivos.GestorVentanas;
import Manejo_Archivos.GestorArchivos;
public class Ventana_agregar_metas extends JFrame implements ActionListener
{
    private JButton boton1,boton2,boton3;
    private JLabel etiqueta1,etiqueta2;
    private JTextField nombre;
    private JTextField descripcion;
    private GestorVentanas gestorVentanas;
    private GestorArchivos gestorArchivos;
    private JScrollPane scroll;
    private Metas metas;

    public Ventana_agregar_metas() {

        //layout
        this.setLayout((LayoutManager)null);
        //botones
        this.boton1 = new JButton("Agregar Meta");
        this.boton1.setBounds(10, 10, 200, 30);
        this.add(this.boton1);
        this.boton1.addActionListener(this);
        this.boton2 = new JButton("Atrás");
        this.boton2.setBounds(230, 10, 100, 30);
        this.add(this.boton2);
        this.boton2.addActionListener(this);
        this.boton3 = new JButton("Ingresar nombre de la Meta");
        this.boton3.setBounds(150,45,200,30);
        this.boton3.addActionListener(this);
        this.add(this.boton3);
        //etiquetas
        this.etiqueta1 = new JLabel("Nombre de la Meta:");
        this.etiqueta1.setBounds(10, 45, 200, 30);
        this.add(this.etiqueta1);
        this.etiqueta2 = new JLabel("Descripción:");
        this.etiqueta2.setBounds(10, 100, 200, 30);
        this.add(this.etiqueta2);
        //JtextField
        this.nombre = new JTextField("");
        this.nombre.setEditable(false);
        //descripcion
        this.descripcion=new JTextField();
        this.descripcion.setBounds (10,150,355,30);
        add(this.descripcion);

        //scroll
        this.scroll= new JScrollPane(this.nombre);
        this.scroll.setBounds(150,80,200,30);
        this.scroll.setFont(new java.awt.Font("Tahoma", 0,14));
        this.add(scroll);
        //clases
        this.metas = new Metas();
        this.gestorArchivos = new GestorArchivos();
        this.gestorVentanas = new GestorVentanas();
    }

    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == this.boton1) {
            if(this.metas.getNombre()==null||this.metas.getNombre()== ""||this.metas.getNombre()==" "){
                JOptionPane.showConfirmDialog(null,"Verifique sus datos","ERROR", JOptionPane.DEFAULT_OPTION,JOptionPane.ERROR_MESSAGE);
                this.metas.setNombre(null);
            }else{ JOptionPane.showConfirmDialog(null,"Meta creada con exito","Éxito!!", JOptionPane.DEFAULT_OPTION);
                this.metas.setDescripcion(this.descripcion.getText());
                this.gestorArchivos.crearArchivo("Metas", this.metas.textoMetas());
                this.nombre.setText("");
                this.descripcion.setText("");
                this.metas.setNombre(null);
            }
            this.metas.setNombre(null);
        }
        if (e.getSource() == this.boton2) {
            gestorVentanas.ejecutarVentanaMetas();
            this.setVisible(false);
        }
        if (e.getSource() == this.boton3) {
            this.metas.setNombre();
            this.nombre.setText(this.metas.getNombre());
        }

    }

}
