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
Para ejecutar ambos programas (tanto el de python como el de go) usar:

```bash
./fuerzaBruta.py 
./fuerzaBruta.go //cambiar esto
```

## 3.Decisiones de diseño
Para probarlo se han usado los dos lenguajes de programación que resultan mas simple para un algoritmo de descifrado usando gpg, pyhton y go. La estructura con la que cuenta este algoritmo es:

-**Función generar contraseña**: Reparte tramos entre hilos para no repetir combinaciones y genera las contraseñas a ser probadas mediante fuerza bruta

-**Función descrifrar**: Prueba la contraseña generada anteriormente e intenta descrifrar con ella el archivo cifrado mediante gpg. Muestra si se ha encontrado o no contraseña, numero de intento y, en el caso de que encuentre, tiempo tardado en encontrarla.

-**Función descifradorClave**: Llama al generador de contraseñas y comprueba si se ha encontrado la contraseña y si debe parar los hilos antes de seguir llamando al generador.

## 4. Solución más rápida
Se ha realizado la prueba para encontrar la contraseña mediante el uso de hilos. Concretamente se han aplicado 3 pruebas: con 4, 9 y 16 hilos. Los resultados obtenidos han sido:

| Hilos | Tiempo empleado (Python) | Tiempo empleado (Go) | Intento (Python) | Intento (Go) |
|:---:|:---:|:---:||:---:||:---:|
| 4  | 2h 49min 42s | ... || 80159 || ... |
| 9  | 1h 15min 11s | ... || 89961 || ... |
| 16 | ... | ... || ... || ... |

## 5.Comparativa de tecnologías.
Comparando python con go tenemos:
