package constantes;

import java.util.Vector;

public class Constantes {
	public static double BILHETE; 
	public static int[]  NUMEROS = {0,0,0,0,0,0};
	public static int    PORTA   = 0;
	public static boolean comeca = false;
	static public void setConst(Vector linha){
		String temp;
		temp  = (String) linha.get(0);
		PORTA = Integer.parseInt(temp.split("=")[1]);
		temp  = (String) linha.get(1);
		for(int i = 0;i<6;i++){
			NUMEROS[i] = Integer.parseInt(temp.split("=")[1].split(",")[i]);			
		}
		temp    = (String) linha.get(2);
		BILHETE = Double.parseDouble(temp.split("=")[1]);
	}
}