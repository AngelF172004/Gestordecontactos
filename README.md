private void guardarContactoEnArchivo(String nombre, String telefono, String email) {
    if (dato == null || dato.isEmpty()) {
        JOptionPane.showMessageDialog(null, "El nombre de usuario no puede estar vacío.", "Error", JOptionPane.ERROR_MESSAGE);
        return;
    }

    if (nombre.isEmpty() || telefono.isEmpty() || email.isEmpty()) {
        JOptionPane.showMessageDialog(null, "Por favor, complete todos los campos.", "Error", JOptionPane.ERROR_MESSAGE);
        return;
    }

    // Ruta del archivo donde se guardan los contactos
    String ruta = "C:\\FICHERO\\" + dato + "\\DATAA.txt";

    try {
        File archivo = new File(ruta);
        
        if (!archivo.exists()) {
            archivo.getParentFile().mkdirs();
            archivo.createNewFile();
        }

        FileWriter crear = new FileWriter(archivo, true);
        PrintWriter escribir = new PrintWriter(crear);

        // Guarda el contacto en formato: nombre, teléfono, email
        escribir.println(nombre + "," + telefono + "," + email);

        escribir.close();
        crear.close();

        JOptionPane.showMessageDialog(null, "Contacto guardado en DATAA.txt.", "Éxito", JOptionPane.INFORMATION_MESSAGE);
    } catch (IOException e) {
        e.printStackTrace();
    }
}

// Se usa en el botón de agregar contacto
private void jButton3ActionPerformed(java.awt.event.ActionEvent evt) {                                         
    String nombre = jTextField1.getText().trim();
    String telefono = jTextField2.getText().trim();
    String email = jTextField3.getText().trim();

    guardarContactoEnArchivo(nombre, telefono, email);

    // Limpiar los campos después de guardar
    jTextField1.setText("");
    jTextField2.setText("");
    jTextField3.setText("");
}
