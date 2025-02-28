
private void jButton5ActionPerformed(java.awt.event.ActionEvent evt) {                                         
    String nombre = jTextField1.getText().trim();
    
    if (nombre.isEmpty()) {
        JOptionPane.showMessageDialog(null, "Debe ingresar un nombre para eliminar.", "Error", JOptionPane.ERROR_MESSAGE);
        return;
    }
    
    String ruta = "C:\\FICHERO\\" + dato + "\\DATAA.txt";
    File archivo = new File(ruta);
    
    if (!archivo.exists()) {
        JOptionPane.showMessageDialog(null, "El archivo de datos no existe.", "Error", JOptionPane.ERROR_MESSAGE);
        return;
    }
    
    boolean eliminado = false;
    StringBuilder nuevosDatos = new StringBuilder();
    
    try (BufferedReader lector = new BufferedReader(new FileReader(archivo))) {
        String linea;
        while ((linea = lector.readLine()) != null) {
            String[] datos = linea.split(",");
            if (!datos[0].equalsIgnoreCase(nombre)) {
                nuevosDatos.append(linea).append("\n");
            } else {
                eliminado = true;
            }
        }
    } catch (IOException e) {
        e.printStackTrace();
    }

    if (eliminado) {
        try (PrintWriter escritor = new PrintWriter(new FileWriter(archivo))) {
            escritor.print(nuevosDatos.toString());
        } catch (IOException e) {
            e.printStackTrace();
        }
        JOptionPane.showMessageDialog(null, "Contacto eliminado correctamente.", "Éxito", JOptionPane.INFORMATION_MESSAGE);
    } else {
        JOptionPane.showMessageDialog(null, "No se encontró el contacto.", "Error", JOptionPane.ERROR_MESSAGE);
    }
}
