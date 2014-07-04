package io;

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.Vector;

public class Arquivo {
	static public Vector carregar(String arquivo){
		Vector <String> linhas = new Vector();
        String str;
		try {
			int i = 0; 
			BufferedReader in = new BufferedReader(new FileReader(arquivo));
	        while ((str = in.readLine()) != null) {
	        	linhas.add(str);
	        	i++;
	        	System.out.println(i);
	        }
	        in.close();
		}catch (IOException e){
			return null;
	    }
		return linhas;
	}
}