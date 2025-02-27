# Gestordecontactos
DefaultTableModel mdlTabla = new DefaultTableModel();
jTable1.setModel(new javax.swing.table.DefaultTableModel(
    new Object [][] {},
    new String [] {"Nombre", "Telefono", "email"}
) {
    Class[] types = new Class [] {
        java.lang.String.class, java.lang.Integer.class, java.lang.String.class
    };

    public Class getColumnClass(int columnIndex) {
        return types [columnIndex];
    }
});
