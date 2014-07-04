package servidor;

import javax.swing.JOptionPane;

import constantes.Constantes;

public class Ativar extends Thread{
	public void run(){
		int a = -1;
		while(true){
    		a = JOptionPane.showConfirmDialog(null, "Aperte sim para começar","Iniciar", 0);
        	if(a==0){
        		Constantes.comeca = true;
        		break;
        	}    		
    	}
	}
}