#gestor de contactos mostar contactos 
private void jButton2ActionPerformed(java.awt.event.ActionEvent evt) {                                         
    limpiarTabla();
    
    String ruta = "C:\\FICHERO\\" + dato + "\\DATAA.txt";

    try {
        FileReader fr = new FileReader(ruta);
        BufferedReader br = new BufferedReader(fr);
        String d;
        DefaultTableModel model = (DefaultTableModel) jTable1.getModel();

        while ((d = br.readLine()) != null) {
            StringTokenizer dato = new StringTokenizer(d, ",");
            Vector<String> x = new Vector<>();
            
            while (dato.hasMoreTokens()) {
                x.addElement(dato.nextToken());
            }
            
            model.addRow(x);
        }

        br.close();
        fr.close();
    } catch (Exception e) {
        JOptionPane.showMessageDialog(null, "Error: " + e.getMessage());
    }
}


