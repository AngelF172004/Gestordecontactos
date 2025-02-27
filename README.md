private void cargarContactosDesdeArchivo() {
    limpiarTabla();
    
    String ruta = "C:\\FICHERO\\" + dato + "\\DATAA.txt";

    try {
        File archivo = new File(ruta);
        
        if (!archivo.exists()) {
            JOptionPane.showMessageDialog(null, "No hay contactos guardados.", "Información", JOptionPane.INFORMATION_MESSAGE);
            return;
        }

        FileReader fr = new FileReader(archivo);
        BufferedReader br = new BufferedReader(fr);
        String linea;
        DefaultTableModel model = (DefaultTableModel) jTable1.getModel();

        while ((linea = br.readLine()) != null) {
            String[] datos = linea.split(",");
            if (datos.length == 3) {
                model.addRow(new Object[]{datos[0], datos[1], datos[2]});
            }
        }

        br.close();
        fr.close();
    } catch (IOException e) {
        JOptionPane.showMessageDialog(null, "Error al cargar los contactos: " + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
    }
}



