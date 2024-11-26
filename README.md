# 1TFIFC33W

          static int buscar(String matricula, String[] colMatris) {
              boolean encontrado = false;
              int i = 0;
              while (i < colMatris.length && !encontrado) {
                  if (colMatris[i].equals(matricula)) {
                      encontrado = true;
                  } else {
                      i = i + 1;
                  }
              }
              return encontrado ? i : -1;
          }
      
          static String[] losAlquilados(int[] recaudacion, String[] colMatris) {
              int longitud = colMatris.length;
              String[] resultado = new String[longitud];
              int j = -1;
              for (int i = 0; i < longitud; i++) {
                  if (recaudacion[i] > 0) {
                      j = j + 1;
                      resultado[j] = colMatris[i] + " " + recaudacion[i];
                  }
              }
              for (int i = j + 1; i < longitud; i++) {
                  resultado[i] = "";
              }
              return resultado;
          }
      
          static void actualizar(int[] recaudacion, String[] colMatris, String matricula, int valor) {
              int posicion = buscar(matricula, colMatris);
              if (posicion > -1) {
                  recaudacion[posicion] = recaudacion[posicion] + valor;
              }
          }
      
          static String[] losAlquiladosOrden(int[] recaudacion, String[] colMatris) {
              int longitud = colMatris.length;
              int[] valor = new int[longitud];
              for (int i = 0; i < longitud; i++) {
                  valor[i] = recaudacion[i];
              }
              String[] resultado = new String[longitud];
              int j = -1;
              boolean hayRecaudacion = true;
              int pos;
              while (hayRecaudacion) {
                  pos = posMasRentable(valor);
                  if (valor[pos] > 0) {
                      j = j + 1;
                      resultado[j] = colMatris[pos] + " " + valor[pos];
                      valor[pos] = 0;
                  } else {
                      hayRecaudacion = false;
                  }
              }
              for (int k = j + 1; k < longitud; k++) {
                  resultado[k] = "";
              }
              return resultado;
          }
