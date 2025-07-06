Ejemplo 2. Simulación en 2D de surfactantes en solución (Ejemplo de LAMMPS)

En la carpeta debe haber los siguientes archivos:
 a) in.micelle
 b) micelle2d.f 
 c) def.micelle

1. El archivo micelle2d.f es un código para generar el archivo de estructura.
   Se debe compilar usando:
 1) gfortran micelle2d.f -o datagen
 2) se generará un ejecutable denominado datagen.

2. Correr el ejecutable usando como archivo de entrada def.micelle y como salida el archivo data.micelle usando:
 1) - ./datagen < def.micelle > data.micelle -

3. Inspecciona los archivos .micelle usando:
 1) less in.micelle
 2) less data.micelle
	- para salir presiona "Q" -

4. Ejecutar lammps usando:
 1) ./lmp_serial < in.micelle

5. Visualizar en Ovito y generar una película para lo cual se debe:
   a) Abrir Ovito.app
   b) Cargar el archivo dump.micelle mediante “Load File”
     - escribir ovito dump.micelle -
   c) Definir tipos y tamaños de partículas en “Particle types”
      Type 1 color blanco y 0.25 de Display radius
      Type 2 color rojo y 0.75 de Display radius
      Type 3 color café y 0.5 de Display radius
      Type 4 color café y 0.5 de Display radius
   d) Activar la casilla “File contains time series”
    - esta casilla siempre se encuentra activa en versiones nuevas -
   e) En la parte superior, presiona la pestaña “Rendering” y selecciona “Complete animation”
   f) En la parte inferior activa "Save to file" y presiona "Choose" para asignar directorio, nombre y formato 
   g) Mas abajo presiona “Render Active Viewport”, espera el 100% para generar el archivo y guarda la sesión ovito

6. Generar un archivo de estructura con 200 surfactantes de longitud 6 (5 # of tails) en una placa de 40 40
   (Abre y modificar como texto el def.micelle y guardarlo como def_2.micelle)

7. Asignar las interacciones par faltantes en el archivo in.micelle;
   se recomienda hacer una copia de texto que éste denominada in_2.micelle y corregir la linea 12 y 70
   # tail/tail - size-averaged and long-range 
     pair_coeff      3 5*7 1.0 0.67 2.5
     pair_coeff      4 5*7 1.0 0.67 2.5
     pair_coeff      5 5*7 1.0 0.67 2.5
     pair_coeff      6 6*7 1.0 0.67 2.5
     pair_coeff      7 7 1.0 0.67 2.5

   # solvent/tail - full-size and repulsive
     pair_coeff      1 5*7 1.0 1.0 1.12246

   # head/tail - size-averaged and repulsive
    pair_coeff      2 5*7 1.0 0.75 1.12246

repetir los pasos 2, 4 y 5... donde:
 1) ./lmp_mpi < in_2.micelle
 2) Type 4 color guinda y 0.5 de Display radius
    Type 5 color azul y 0.5 de Display radius
    Type 6 color verde y 0.5 de Display radius
    Type 7 color gris y 0.5 de Display radius