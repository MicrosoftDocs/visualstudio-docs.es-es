---
title: "Depuración remota multiplataforma con Herramientas de Python para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 7634da4bdc2b0186f410acb4eaf57a70ddea3e91
ms.lasthandoff: 03/10/2017

---

# <a name="remotely-debugging-python-code"></a>Código de Python de depuración remota

La utilidad Herramientas de Python para Visual Studio (PTVS) puede iniciar y depurar aplicaciones de Python de manera local y remota en una máquina de Windows (consulte [Depuración remota](../debugger/remote-debugging.md)). También puede realizar la depuración remota en un sistema operativo, un dispositivo o una implementación de Python diferentes a CPython mediante la [biblioteca ptvsd](https://pypi.python.org/pypi/ptvsd).

Al usar ptvsd, el código de Python que se depura hospeda el servidor de depuración al que puede asociar Visual Studio. Para ello se necesita una pequeña modificación en el código para importar y habilitar al servidor, y puede que sean necesarias configuraciones de la red o del firewall en la máquina remota para permitir conexiones TCP.

Para ver una introducción a la depuración remota, consulte el vídeo de youtube.com (6 minutos y 22 segundos)[Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc) (Profundización: depuración remota entre plataformas).

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="preparing-the-script-for-debugging"></a>Preparación del script para la depuración

1. Cree un archivo de Python con el código siguiente en la máquina remota:

  ```python
  import random

  guesses_made = 0
  name = raw_input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print 'Well, {0}, I am thinking of a number between 1 and 20.'.format(name)

  while guesses_made < 6:
      guess = int(raw_input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print 'Your guess is too low.'
      if guess > number:
          print 'Your guess is too high.'
      if guess == number:
          break
  if guess == number:
      print 'Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made)
  else:
      print 'Nope. The number I was thinking of was {0}'.format(number)
  ```
 
1. Instale el paquete `ptvsd` en su entorno mediante `pip install ptvsd`.

1. Habilite la depuración remota; para ello, agregue el código siguiente al punto más anterior posible del script, delante de otro código. (Aunque no es un requisito estricto, es imposible depurar subprocesos en segundo plano generados antes de la llamada a la función `enable_attach`).

   ```python
   import ptvsd
   ptvsd.enable_attach(secret='my_secret')
   ```

   El parámetro `secret` pasado a `enable_attach` se usa para restringir el acceso al script en ejecución. Al realizar la asociación, tendrá que especificarlo en Visual Studio o se denegará la conexión. Para evitar esto y permitir que todos se puedan conectar, use `enable_attach(secret=None)`.

1. Guarde el archivo e inicie el script en la máquina remota. Tenga en cuenta que la llamada a `enable_attach` se ejecuta en segundo plano y que espera las conexiones entrantes. Si lo desea, se puede llamar a la función `wait_for_attach` después de `enable_attach` para bloquear el programa hasta que se asocie el depurador.

Además de `enable_attach` y `wait_for_attach`, ptvsd también proporciona una función auxiliar `break_into_debugger`, que actúa como un punto de interrupción de programación si el depurador está asociado. También hay una función `is_attached` que devuelve `True` si el depurador está asociado (tenga en cuenta que no es necesario comprobar este resultado antes de llamar a cualquier otra función `ptvsd`).

## <a name="attaching-remotely-from-python-tools"></a>Asociación remota desde Herramientas de Python

En estos pasos, estableceremos un punto de interrupción simple para detener el proceso remoto.

1. Cree una copia del archivo remoto en la máquina local y ábralo en Visual Studio. No importa dónde se encuentre el archivo, pero su nombre debe coincidir con el nombre del script en la máquina remota a la que se asociará.

1. Seleccione **Depurar > Asociar a proceso** para abrir el cuadro de diálogo "Asociar a proceso".

1. Establezca **Transporte** en **Depuración remota de Python**.

1. Escriba la dirección de la máquina remota en el campo **Calificador** y presione Entrar. Se mostrarán los procesos disponibles en esa máquina:

![Inserción del calificador y enumeración de los procesos](media/remote-debugging-qualifier.png)

1. Un error en esta etapa normalmente indica que el secreto no coincide, la versión de `ptvsd` no coincide con la que usa PTVS o no se ha podido establecer una conexión. Una de las causas comunes de no poder conectar es que la máquina remota tenga un firewall que está impidiendo que se abra el puerto del servidor de depuración (el predeterminado es 5678). Puede volver a configurar el firewall o usar un puerto diferente; para esto último, especifíquelo explícitamente en la llamada a `enable_attach` en el parámetro `address`, por ejemplo:

  ```python
  ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))
  ```

  El formato de dirección es el mismo que el usado por el socket de módulo de Python estándar para los sockets de tipo `AF_INET`; consulte su [documentación](http://docs.python.org/3/library/socket.html#socket-families) para más información. 

1. Cuando el proceso aparezca en la lista, haga doble clic en él para asociarlo. Visual Studio muestra sus herramientas de depuración mientras el script se sigue ejecutando. Para el script de ejemplo mostrado anteriormente, al escribir un número se llegará al punto de interrupción:

    ![Se ha llegado al punto de interrupción](media/remote-debugging-breakpoint-hit.png)

1. En este momento, puede usar todas las características de depuración habituales de PTVS. 

1. Al detener la depuración, Visual Studio se desasocia de su script, pero este se sigue ejecutando en la máquina remota. El servidor de depuración también continúa ejecutándose en el subproceso en segundo plano, por lo que puede volver a asociar al proceso en otro momento mediante el mismo procedimiento.


## <a name="securing-the-debugger-connection-with-ssl"></a>Protección de la conexión del depurador con SSL

De forma predeterminada, la conexión al servidor de depuración remota de PTVS no está protegida de ninguna forma; cualquiera que tenga el secreto puede conectarse y todos los datos se pasan como texto sin formato. Por lo tanto, otros usuarios de la red pueden consultar los datos o incluso ejecutar un ataque de tipo man in the middle (MITM). Para evitar esto cuando la depuración se realiza a través de redes no seguras o Internet, el servidor de depuración admite SSL. 

Para proteger el canal con SSL, necesitará un certificado SSL. Puede generar un certificado autofirmado, como se describe en la [documentación del módulo estándar de Python `ssl` ](http://docs.python.org/3/library/ssl.html#self-signed-certificates). Para evitar ataques MITM, dicho certificado generado también tendrá que agregarse al almacén raíz de CA en la máquina de Windows donde se ejecuta PTVS. Para ello, se puede usar el Administrador de certificados (certmgr.msc) como se describe en [How do I export certificates and/or private keys?](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/how-do-i-export-certificates-andor-private-keys/7722900a-e848-4076-bc50-9e2f5e3c66ac) (¿Cómo exportar certificados o claves privadas?). Tenga en cuenta que debe tener otro archivo de certificado (no combinado con la clave privada en un único archivo) para importarlo. 

Una vez que tiene generados y registrados el certificado y los archivos de clave privada, deberá actualizar la llamada a `enable_attach` en su script para poder usarlos. Esto se realiza por medio de los parámetros `certfile` y `keyfile`, que tienen el mismo significado que para la función estándar de Python `ssl.wrap_socket`. Por ejemplo, si el archivo de certificado se denomina `my_cert.cer` y el archivo de clave se denomina `my_cert.key`, use: 

```python
ptvsd.enable_attach(secret='my_secret', certfile='my_cert.cer', keyfile='my_cert.key')
```

El proceso de asociación es exactamente el mismo que se describió anteriormente, salvo que, en lugar de usar el esquema `tcp://` del calificador, use `tcps://`: 

![Selección del transporte de depuración remota con SSL](media/remote-debugging-qualifier-ssl.png)

Si no se agregó el certificado al almacén raíz de CA, obtendrá un mensaje de advertencia: 

![Advertencia de certificado SSL](media/remote-debugging-ssl-warning.png)

Puede optar por ignorar el mensaje y continuar con la depuración; el canal seguirá cifrado contra el espionaje, pero al ignorar la advertencia queda expuesto a la posibilidad de un ataque MITM.

