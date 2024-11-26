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

              public static int[][] multiplicar(int[][] m1, int[][] m2) {
        int filas1 = m1.length;
        int cols1 = m1[0].length;
        int filas2 = m2.length;
        int cols2 = m2[0].length;

        // Verificar si las matrices pueden multiplicarse
        if (cols1 != filas2) {
            throw new IllegalArgumentException(
                "El número de columnas de la primera matriz debe coincidir con el número de filas de la segunda");
        }

        int[][] producto = new int[filas1][cols2];

        // Bucle para realizar la multiplicación
        for (int i = 0; i < filas1; i++) {
            for (int j = 0; j < cols2; j++) {
                int prod = 0;
                for (int k = 0; k < cols1; k++) {
                    prod += m1[i][k] * m2[k][j];
                }
                producto[i][j] = prod;
            }
        }

        return producto;
    }

    private static void pintarMatriz(int[][] matriz) {
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                System.out.print(matriz[i][j] + " ");
            }
            System.out.println();
        }
    }
