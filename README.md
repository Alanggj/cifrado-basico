# Descifrador Automatico — Cesar & Atbash

Aplicacion web que intenta descifrar texto de forma automatica probando Cesar y Atbash sobre un conjunto de caracteres personalizable basado en ASCII.

**Demo en vivo:** [cifradorclasico.netlify.app](https://cifradorclasico.netlify.app)

**Demo secundario** [cifradorclasico.cloudflare](https://cifrado-basico.al351914.workers.dev)

---

## Que hace

- Detecta automaticamente si el texto parece estar cifrado con **Cesar** o **Atbash**
- Calcula el desplazamiento probable cuando el resultado parece ser **Cesar**
- Usa pistas de texto de examen, incluyendo patrones como **Punto/Puntos:** al inicio o al final
- Analiza el texto **linea por linea** para examenes mixtos (lineas claras + lineas cifradas)
- Si una linea no es concluyente, muestra alternativas para revision manual
- Incluye un boton para ver una **tabla con todas las combinaciones** (Sin cifrar, Cesar por shift y Atbash), resaltando las mas probables
- Permite definir el **conjunto de caracteres** que participan en el descifrado (el "alfabeto"), totalmente personalizable
- Los caracteres fuera del conjunto pasan sin modificacion al resultado
- Muestra un porcentaje de confianza para el resultado detectado
- Incluye botones para copiar el resultado y para usarlo como nueva entrada

---

## Como usarlo

1. Abre [cifradorclasico.netlify.app](https://cifradorclasico.netlify.app) o el archivo `index.html` directamente en tu navegador
2. Edita el campo **Conjunto de caracteres** si necesitas un alfabeto diferente al predeterminado
3. Escribe tu mensaje cifrado en el campo de texto
4. Presiona **Descifrar automático**. El sistema devuelve el resultado con el algoritmo y la confianza detectados

---

## Algoritmos implementados

### Cesar

El sistema prueba todos los desplazamientos posibles dentro del charset y escoge el resultado que mejor coincide con texto en espanol.

La puntuacion incluye frecuencia de letras, palabras comunes y patrones tipicos de examen como "Punto:" o "Puntos: 10".

```
caracter_descifrado = charset[ (indice - shift + N) mod N ]
```

### Atbash

Invierte el charset: el primer caracter se convierte en el ultimo, el segundo en el penultimo, etc.

```
caracter_cifrado = charset[ (N - 1) - indice ]
```

El resultado final se elige automaticamente entre Cesar y Atbash.

---

## Estructura del proyecto

```
index.html   — Interfaz de usuario y logica JavaScript
style.css    — Estilos (tema oscuro)
```

---

## Contexto academico

Practica 1 — Seguridad en Sistemas — 2026  
Alaan Gael Gallardo Jimenez — ID: 351914

> Esta practica tiene proposito educativo. El Cifrado Cesar y el Cifrado Atbash son vulnerables
> al analisis de frecuencias descrito por Al-Kindi en el siglo IX y no deben usarse para
> proteger informacion real.
