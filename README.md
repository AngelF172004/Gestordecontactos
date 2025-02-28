private void jButton4ActionPerformed(java.awt.event.ActionEvent evt) {                                         
    String nombre = jTextField1.getText().trim();
    
    if (nombre.isEmpty()) {
        JOptionPane.showMessageDialog(null, "Debe ingresar un nombre para buscar.", "Error", JOptionPane.ERROR_MESSAGE);
        return;
    }
    
    String ruta = "C:\\FICHERO\\" + dato + "\\DATAA.txt";
    File archivo = new File(ruta);
    
    if (!archivo.exists()) {
        JOptionPane.showMessageDialog(null, "El archivo de datos no existe.", "Error", JOptionPane.ERROR_MESSAGE);
        return;
    }
    
    boolean encontrado = false;
    
    try (BufferedReader lector = new BufferedReader(new FileReader(archivo))) {
        String linea;
        while ((linea = lector.readLine()) != null) {
            String[] datos = linea.split(",");
            if (datos[0].equalsIgnoreCase(nombre)) {
                jTextField1.setText(datos[0]);
                jTextField2.setText(datos[1]);
                jTextField3.setText(datos[2]);
                encontrado = true;
                break;
            }
        }
    } catch (IOException e) {
        e.printStackTrace();
    }
    
    if (encontrado) {
        JOptionPane.showMessageDialog(null, "Contacto encontrado.", "Éxito", JOptionPane.INFORMATION_MESSAGE);
    } else {
        JOptionPane.showMessageDialog(null, "No se encontró el contacto.", "Error", JOptionPane.ERROR_MESSAGE);
    }
}


