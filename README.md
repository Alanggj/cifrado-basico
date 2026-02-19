# Cifrado Clasico — Cesar & Atbash

Aplicacion web que implementa dos algoritmos de cifrado clasico sobre un conjunto de caracteres personalizable basado en ASCII.

**Demo en vivo:** [cifradorclasico.netlify.app](https://cifradorclasico.netlify.app)

---

## Que hace

- Cifra y descifra texto usando el **Cifrado Cesar** con desplazamiento (shift) configurable
- Cifra y descifra texto usando el **Cifrado Atbash** (inversion del alfabeto)
- Permite definir el **conjunto de caracteres** que participan en el cifrado (el "alfabeto"), totalmente personalizable
- Los caracteres fuera del conjunto pasan sin modificacion al resultado
- Muestra el modulo N (tamano del charset) en tiempo real
- Incluye botones para copiar el resultado y para usarlo como nueva entrada

---

## Como usarlo

1. Abre [cifradorclasico.netlify.app](https://cifradorclasico.netlify.app) o el archivo `index.html` directamente en tu navegador
2. Selecciona el modulo: **Cifrado Cesar** o **Cifrado Atbash**
3. Edita el campo **Conjunto de caracteres** si necesitas un alfabeto diferente al predeterminado
4. En Cesar, ajusta el **Desplazamiento (shift)**
5. Escribe tu mensaje en el campo de texto
6. Presiona **Cifrar** o **Descifrar**

---

## Algoritmos implementados

### Cifrado Cesar

Desplaza cada caracter del texto una cantidad fija `shift` de posiciones dentro del charset.

```
caracter_cifrado = charset[ (indice + shift) mod N ]
caracter_descifrado = charset[ (indice - shift + N) mod N ]
```

El shift se normaliza con `((shift % N) + N) % N` para soportar valores negativos y mayores que N.

### Cifrado Atbash

Invierte el charset: el primer caracter se convierte en el ultimo, el segundo en el penultimo, etc.

```
caracter_cifrado = charset[ (N - 1) - indice ]
```

Al ser simetrico, cifrar y descifrar usan la misma operacion.

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
