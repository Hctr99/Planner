package Clases_Dominio;
import javax.swing.*;
import Manejo_Archivos.GestorArchivos;

public class Metas {
    private String nombre;
    private String descripcion;
    private GestorArchivos gestorArchivos;

    public Metas() {
        this.nombre = "";
        this.descripcion = "";
        this.gestorArchivos = new GestorArchivos();
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre() {
        String input = JOptionPane.showInputDialog(null, "Ingrese el nombre de la Meta");
        this.nombre=input;
        }


    public String getDescripcion() {
        return descripcion;
    }

    public void setDescripcion(String descripcion) {
        this.descripcion = descripcion;
    }

    public String textoMetas(){
        String textoA = this.gestorArchivos.contarLineas("Metas")+"|" +" Nombre: "+this.nombre+ " Descripción: "+this.descripcion;
        return textoA;
    }
}
