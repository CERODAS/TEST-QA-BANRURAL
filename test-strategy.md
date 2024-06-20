1. Al iniciar el proyecto no funcionaba nada y en consola mostraba un error porque la funcion guessSubmit.addeventListener no la estaba encontrando, el motivo es porque estaba mal escrita, se corrige ya que la forma correcta de escribirla es utilizando camel case y se escribe de la siguiente manera: guessSubmit.addEventListener.

2. Al ingresar algun numero y presionar el boton mostraba un error en consola porque no encontraba la funcion lowOrHi.textContent = 'El número es menor!'; y era debido a que en la declaracion de la constante lowOrHi se esta inicializando la constante pero no se le estaba indicando por medio de que atributo tenia que identificar el objeto creado ya que la linea era: const lowOrHi = document.querySelector('lowOrHi'); y la manera correcta es: const lowOrHi = document.querySelector('.lowOrHi');

3. Al presionar el boton para ingresar el numero mostraba otro error y era similar al primero pues se estaba utilizando la funcion correspondiente de la manera siguiente: resetButton.addeventListener('click', resetGame); y la forma correcta de escribirla es: resetButton.addEventListener('click', resetGame);

4. al ingresar un numero mayor o menor al que se tiene que adivinar si esta mostrando la alerta correspondiente pero la muestra de color verde y debe ser de color negro, y es debido a que el fragmento de codigo que lo realiza estaba asi: 
    lastResult.textContent = 'Incorrecto! ';
    lastResult.style.backgroundColor = 'green';
    if(userGuess < randomNumber) {
       lowOrHi.textContent = 'El número es mayor!';
    }else if(userGuess > randomNumber) {
       lowOrHi.textContent = 'El número es menor!';
    }

y deberia ser asi: 
    lastResult.textContent = 'Incorrecto! ';
    lastResult.style.backgroundColor = 'black';
    if(userGuess < randomNumber) {
      lowOrHi.textContent = 'El número es mayor!';
    } else if(userGuess > randomNumber) {
       lowOrHi.textContent = 'El número es menor!';
    }

5. Si se logra adivinar el numero se esta mostrando el mensaje correspondiente pero en color rojo y deberia ser verde, ademas sigue apareciendo el mensaje que es mayor o menor y era debido a que el fragmento de codigo que lo realiza estaba asi: 
    lastResult.textContent = 'Felicitaciones! adivinaste el número!';
    lastResult.style.backgroundColor = 'red';
    setGameOver();

y deberia ser asi: 
    lastResult.textContent = 'Felicitaciones! adivinaste el número!';
    lastResult.style.backgroundColor = 'green';
    lowOrHi.textContent = '';
    setGameOver();

6. Se estan generando numero aleatorios pero solamente del 1 al 10 y deberia ser del 1 al 100, por lo que se corrige el fragmento de codigo ya que estaba asi: 
    let randomNumber = Math.random() * 10;

y deberia ser asi: 
    let randomNumber = Math.floor(Math.random() * 100) + 1;

7. Se tenia establecidos solo 5 intentos pero deben ser 10, estaba de esta manera: 
    const ATTEMPS = 10;

y debe estar de esta manera: 
    const ATTEMPS = 10;

8. El condiciona esta incorrecto pues primero esta comparando si el numero ingresado es igual al numero a adivinar, si lo es que muestre la alerta que perdio, y que si el contador de intentos es igual a los intentos permitidos que adivino el numero, estaba de la siguiente manera: 
    if(userGuess === randomNumber){
        lastResult.textContent = '!!!Pérdistes!!!';
        lastResult.style.backgroundColor = 'red';
        lowOrHi.textContent = '';
        setGameOver();
    }else if(guessCount === ATTEMPS){
        lastResult.textContent = 'Felicitaciones! adivinaste el número!';
        lastResult.style.backgroundColor = 'green';
        lowOrHi.textContent = '';
        setGameOver();
    }

y debe ser de la siguiente manera: 
    if(guessCount === ATTEMPS){
        lastResult.textContent = '!!!Pérdistes!!!';
        lastResult.style.backgroundColor = 'red';
        lowOrHi.textContent = '';
        setGameOver();
    }else if(parseInt(userGuess) === randomNumber){
        lastResult.textContent = 'Felicitaciones! adivinaste el número!';
        lastResult.style.backgroundColor = 'green';
        lowOrHi.textContent = '';
        setGameOver();
    }

9. Si se llega al maximo de intentos permitidos sin adivinar debe mostrarse la alerta en color rojo pero se esta mostrando en color negro, el codigo estaba de la siguiente manera: 
    lastResult.textContent = '!!!Pérdistes!!!';
    lastResult.style.backgroundColor = 'black';

y debe ser de la siguiente manera: 
    lastResult.textContent = '!!!Pérdistes!!!';
    lastResult.style.backgroundColor = 'red';

10. Si el usuario adivina el numero muestra la alerta de error se corrige pues en la comparacion se debe tener el tipo de dato exactamente igual que la variable del numero a adivinar, el codigo estaba asi: 
    else if(userGuess === randomNumber)

y debe estar asi: 
    else if(parseInt(userGuess) === randomNumber)

11. No se esta validando si lo que el usuario esta ingresando es un numero entero, se agrega validacion utilizando una expresion regular, se crea la variable con la expresion regular y luego se hace la validacion para saber si es un entero o no: 
    const expresionRegular = /^(?:\d|\-?\d)(?:\d)*$/;
    if(!expresionRegular.test(userGuess)){
      lowOrHi.textContent = 'El valor ingresado no es un número entero';
    }

12. al adivinar el numero y volver a iniciar el juego no se reinicia el numero o no se esta generando uno aleatorio entre 1 al 100, el codigo estaba asi:
    randomNumber = Math.floor(Math.random()) + 1;

y debe ser de la siguiente manera: 
    randomNumber = Math.floor(Math.random() * 100) + 1;