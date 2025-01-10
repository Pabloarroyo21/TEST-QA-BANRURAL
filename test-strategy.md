# ERROR 1: 
Descripcion: En la linea 44 del JS, no especifica el numero maximo de numeros para adivinar que son 100
Codigo erroneo:  let randomNumber = Math.random() * 10;
Correcion:    let randomNumber = Math.floor(Math.random() * 100) + 1
Explicacion de solucion: Especificar el maximo de numeros enteros que se pueden utilizar; 
Se le agrega un ¨+ 1¨ para dezplazar el rango final de 0-99 a 1-100, sumando 1 a cada número. Así:
0 → 1
23 → 24
99 → 100

# ERROR 2:
Descripcion: En la linea 45 del JS, solo se le agregan 5 intentos cuando son 10 los intentos
Codigo erroneo:  const ATTEMPS = 5;
Correcion:    const ATTEMPS = 10;
Explicacion de solucion: Se le corrige el No. de intentos a 10.

# ERROR 3:
Descripcion: La funcion ¨checkGuess¨ No especifica que solo se puede escribir numeros enteros ni tampoco hace la denegacion del ¨.¨ para no poder utilizarlo
Codigo erroneo:  function checkGuess() 
Correcion:    if (userGuess.includes('.')) { 
        lastResult.textContent = 'Por favor, ingresa solo números enteros (sin puntos decimales).';
        lastResult.style.backgroundColor = 'red';
        guessField.value = '';
        guessField.focus();
        return; 
    }
    userGuess = parseInt(userGuess, 10);
Explicacion de solucion: 1.Se bloquea el punto para bloquear numeros con decimales.
                         2.Se agrega el texto en pantalla de que no se pueden utilizar decimales si el usuario coloca el numero ya mencionado y se le agrega el color rojo requerido.
                         3.La línea ¨userGuess = parseInt(userGuess, 10);¨ asegura que el valor ingresado sea tratado como un número entero válido para las comparaciones y cálculos posteriores

# ERROR 5:
Descripcion: En el ¨setGameOver();¨ apartir de la linea 68 a la 72 tenia el mensaje equivocado ya que dice que adivino el numero pero es lo contrario.
Codigo erroneo:    setGameOver();
     else if(guessCount === ATTEMPS) 
      lastResult.textContent = 'Felicitaciones! adivinaste el número!';
      lastResult.style.backgroundColor = 'red';
      setGameOver();
Correcion:      setGameOver();
     else if(guessCount === ATTEMPS) 
      lastResult.textContent = '!!!Pérdistes!!!';
      lastResult.style.backgroundColor = 'red';
      setGameOver();
Explicacion de solucion: Se remplazo el texto de ¨Felicitaciones! adivinaste el número!¨ por el de ¨!!!Pérdistes!!!¨

# ERROR 6:
Descripcion: En la condicion ¨else¨ apartir de la linea 73 a la 77 tenia el color y el mensaje equivocado
Codigo erroneo:   else 
      lastResult.textContent = 'Incorrecto! ';
      lastResult.style.backgroundColor = 'green';
      if(userGuess < randomNumber) 
        lowOrHi.textContent = 'El número es mayor!';
Correcion:  else 
     /* lastResult.textContent = 'Incorrecto! ';
      lastResult.style.backgroundColor = 'BLACK';*/
      if(userGuess < randomNumber) 
        lastResult.textContent = 'Incorrecto! El número es mayor!';
Explicacion de solucion: Se corrigio el texto de cuando el usuario se equivoca y ahora da la pista al equivocarse y se cambio el color de verde al negro.

# ERROR 7:
Descripcion: Se cambio la funcion ¨resetgame¨ del boton de reinicio ya que generaba error al utilizar de nuevo las funciones y tambien generaba el mismo numero.
Codigo erroneo:  function resetGame() {
	  guessCount = 1;

	  const resetParas = document.querySelectorAll('.resultParas p');
	  for(let i = 0; i < resetParas.length; i++) {
		  resetParas[i].textContent = '';
	  }
	  resetButton.parentNode.removeChild(resetButton);

	  guessField.disabled = false;
	  guessSubmit.disabled = false;
	  guessField.value = '';
	  guessField.focus();

	  lastResult.style.backgroundColor = 'white';

	  randomNumber = Math.floor(Math.random()) + 1;
  }
Correcion:    function setGameOver() {
	  guessField.disabled = true;
	  guessSubmit.disabled = true;
	  resetButton = document.createElement('button');
	  resetButton.textContent = 'Comienza un nuevo juego';
	  document.body.appendChild(resetButton);
	  resetButton.addEventListener('click', resetGame);
  }

  function resetGame() {
	  location.reload();
  }
Explicacion de solucion: Ahora el boton de ¨comenzar de nuevo¨ en vez de empezar de nuevo el codigo, ahora recarga de nuevo la pagina para evitar que el codigo no funcione bien y asi empezar con otro numero completamente aleatorio. 



