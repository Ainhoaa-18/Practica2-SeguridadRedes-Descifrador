# Practica2-SeguridadRedes-Descifrador

## 1.Entorno para la ejecución del programa (Python)

Para ejecutar el programa en python tenemos que abrir un entorno venv para que nos deje utilizar las liberias gpg importadas para el descifrado. Los comandos y su orden a ejecutar son:

```bash
  python3 -m pip install python-gnupg
  sudo apt install python3-venv
  python3 -m venv venv
  source venv/bin/activate
```

## 2.Ejecución del programa
Para ejecutar el programa usar:

```bash
./fuerzaBruta.py 

```
Es importante, antes de ejecutar dicho comando, haber activado el venv que se define en el punto 1.

## 3.Decisiones de diseño
Para probarlo se han usado python al ser un lenguaje fácil que permite crear un algoritmo de fuerza bruta de una manera muy sencilla para descifrar archivos gpg. La estructura con la que cuenta este algoritmo es:

-**Función generar contraseña**: Reparte tramos entre hilos para no repetir combinaciones y genera las contraseñas a ser probadas mediante fuerza bruta

-**Función descrifrar**: Prueba la contraseña generada anteriormente e intenta descrifrar con ella el archivo cifrado mediante gpg. Muestra si se ha encontrado o no contraseña, numero de intento y, en el caso de que encuentre, tiempo tardado en encontrarla.

-**Función descifradorClave**: Llama al generador de contraseñas y comprueba si se ha encontrado la contraseña y si debe parar los hilos antes de seguir llamando al generador.

## 4. Pruebas en la ejecución
Se ha realizado la prueba para encontrar la contraseña mediante el uso de hilos para mayor concurrencia y unos tiempos más pequeños y óptimos. Concretamente se han aplicado 3 pruebas: con 4, 9 y 16 hilos. Los resultados obtenidos han sido:

| Hilos | Tiempo empleado (Python) | Intento (Python) |
|:-----:|:------------------------:|:----------------:|
| 4     | 2h 49min 42s             | 80159            |
| 9     | 1h 15min 11s             | 89961            |
| 16    | 1h 9min 28s              | 90274            |

## 5.Conclusiones
Se selecciono un numero de hilos adecuado al tamaño del problema (es decir, seleccione 9 para que haya un reparto de 3 letras por hilo ya que contamos con 27 letras). A partir de ahí se probo con diferentes números de hilos, concretamente 4 y 16, para probar con un numero inferior y superior a 9 hilos. Observando la tabla anterior, como resultado podemos concluir que, aunque por una diferencia de tiempo muy pequeña, gana la opción de 16 hilos, encontrando la contraseña en un tiempo eficiente de 1h 9min y 28s. El número de intentos en comparación con 9 hilos también es pequeño, pero en el caso de 16 podemos ver que se encuentra en más intentos pero menos tiempo, por lo que en el caso de 16 hemos sido capaces de crear muchos más intentos de contraseñas en un tiempo menor.
