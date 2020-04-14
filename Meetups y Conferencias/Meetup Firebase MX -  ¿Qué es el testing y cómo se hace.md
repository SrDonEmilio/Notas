# ¿Qué es testing y cómo se hace?

Héctor Bliss / Meetup Firebase MX - 03/04/2020

---

Cuando estamos empezando, no vemos el testing como algo esencial, pero una vez que lo conoces, cambia tu perspectiva

## ¿Por qué no se hace testing?

¿Podemos culpar al PM por exigirnos el feature sin haberlo provado por el tiempo o es negligencia por parte nuestra? En parte podría considerarse en poco culpa de ambos. Quizá hay que exigirle al PM más tiempo para ir cambiando la filosofía de trabajo.

## Testing mientras codeas

Una buena práctica es ir haciendo las pruebas y pensando en las pruebas mientras se va programando para hacer una mejor programación, aunque lleva mucho más tiempo; hay que evitar hacer falsos testing solo para que pase la prueba, propiciando futuros errores.

## Tipos de Pruebas

### Pruebas Unitarias

Es probar los pequeños componentes/bloques del código, haciendo pruebas muy específicas. Normalmente se prubas las funciones del código, aunque anteriormente se testeaba las classes, era una práctica más universal pero se ha ido cambiando a las funciones.



---

**¿Qué se debe de testear?**

Todos los nuevos features se deberían de testear, aunque sí es tedioso. Sin embargo, puedes recurrir a otro tipos de pruebas para agilizar el testing, dependiendo de las funcionalidades (ojo, no funciones) y flujos del software. Pero es una desición que debe de tomar el equipo o el programador.

---



> Dependiendo la herramienta que estés usando, debes de pensar tu test



---

**¿Cómo se debe de Testear?**

Depende del tipo de equipo que se tenga y del flujo que se tenga. 

---



## TDD

*Test-Driver-Development*

Primero construyes un test y luego codeas para para poder pasar ese test, asegurandote que tú código va a estar bien.





## Herramientas y Recursos

- NextJS - React Framework for Apps
- Enzyme - Testing in React
- [Curso Testing Javascript](testingjavascript.com)
- [Cheat Sheet React Testing Library](https://testing-library.com/docs/react-testing-library/cheatsheet)
