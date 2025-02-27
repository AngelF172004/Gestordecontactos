# Gestordecontactos
private void jButton3ActionPerformed(java.awt.event.ActionEvent evt) {
    Point location = this.getLocation();
    this.setVisible(false);
    
    Pag3 m2 = new Pag3();
    m2.setNombreUsuario2(dato);
    
    m2.setLocation(location);
    m2.setVisible(true);
}
