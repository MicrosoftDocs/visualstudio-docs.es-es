---
title: "Depuración remota multiplataforma de Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/4/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: fa3d69cbb34a61a327d0b4c27430ff04b670a568
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---

# <a name="remotely-debugging-python-code"></a>Código de Python de depuración remota

Visual Studio puede iniciar y depurar aplicaciones de Python de manera local y remota en un equipo Windows (vea [Depuración remota](../debugger/remote-debugging.md)). También puede realizar la depuración remota en un sistema operativo, un dispositivo o una implementación de Python diferentes a CPython mediante la [biblioteca ptvsd](https://pypi.python.org/pypi/ptvsd).

Al usar ptvsd, el código de Python que se depura hospeda el servidor de depuración al que puede asociar Visual Studio. Para ello se necesita una pequeña modificación en el código para importar y habilitar al servidor, y puede que sean necesarias configuraciones de la red o del firewall en la máquina remota para permitir conexiones TCP.

Para ver una introducción a la depuración remota, consulte el vídeo de youtube.com (6 minutos y 22 segundos)[Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc) (Profundización: depuración remota entre plataformas).

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="setting-up-a-linux-machine"></a>Configuración de un equipo Linux

Para seguir este tutorial, necesitará lo siguiente:

- Un equipo remoto que ejecute Python en un sistema operativo como Mac OSX o Linux.
- El puerto 5678 (entrada) abierto en el firewall de ese equipo, que es el valor predeterminado para la depuración remota.

Puede crear fácilmente [máquinas virtuales de Linux en Azure](https://docs.microsoft.com/azure/virtual-machines/linux/creation-choices) y [tener acceso mediante Escritorio remoto](https://docs.microsoft.com/azure/virtual-machines/linux/use-remote-desktop) desde Windows. El uso de Ubuntu para la máquina virtual resulta útil porque Python está instalado de forma predeterminada; de lo contrario, vea la lista en [Selección e instalación de los intérpretes de Python](python-environments.md#selecting-and-installing-python-interpreters) para obtener ubicaciones adicionales de descarga de Python.

Para obtener detalles sobre cómo crear una regla de firewall para una máquina virtual de Azure, vea [Apertura de puertos para una máquina virtual en Azure mediante Azure Portal](https://docs.microsoft.com/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="preparing-the-script-for-debugging"></a>Preparación del script para la depuración

1. En el equipo remoto, cree un archivo de Python denominado `guessing-game.py` con el código siguiente:

  ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
    guess = int(input('Take a guess: '))
    guesses_made += 1
    if guess < number:
        print('Your guess is too low.')
    if guess > number:
        print('Your guess is too high.')
    if guess == number:
        break
    if guess == number:
    print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
    print('Nope. The number I was thinking of was {0}'.format(number))
  ```
 
1. Instale el paquete `ptvsd` en su entorno mediante `pip3 install ptvsd`. (Nota: Es una buena idea registrar la versión de ptvsd que se instala en caso de necesitarla para solucionar problemas; la [lista de ptvsd](https://pypi.python.org/pypi/ptvsd) también muestra las versiones disponibles).

1. Habilite la depuración remota agregando el código siguiente al punto más anterior posible de `guessing-game.py`, delante de otro código. (Aunque no es un requisito estricto, es imposible depurar subprocesos en segundo plano generados antes de la llamada a la función `enable_attach`).

   ```python
   import ptvsd
   ptvsd.enable_attach('my_secret')
   ```

   El primer argumento pasado a `enable_attach` (denominado "secreto") restringe el acceso al script en ejecución, y deberá escribir este secreto al adjuntar el depurador remoto. (Aunque no se recomienda, puede permitir que cualquiera se conecte, mediante `enable_attach(secret=None)`).

1. Guarde el archivo y ejecute `python3 guessing-game.py`. La llamada a `enable_attach` se ejecuta en segundo plano y espera las conexiones entrantes mientras se interactúa con el programa. Si lo desea, se puede llamar a la función `wait_for_attach` después de `enable_attach` para bloquear el programa hasta que se asocie el depurador.

> [!Tip]
> Además de `enable_attach` y `wait_for_attach`, ptvsd también proporciona una función auxiliar `break_into_debugger`, que actúa como un punto de interrupción de programación si el depurador está asociado. También hay una función `is_attached` que devuelve `True` si el depurador está asociado (tenga en cuenta que no es necesario comprobar este resultado antes de llamar a cualquier otra función `ptvsd`).

## <a name="attaching-remotely-from-python-tools"></a>Asociación remota desde Herramientas de Python

En estos pasos, estableceremos un punto de interrupción simple para detener el proceso remoto.

1. Cree una copia del archivo remoto en la máquina local y ábralo en Visual Studio. No importa dónde se encuentre el archivo, pero su nombre debe coincidir con el nombre del script en la máquina remota a la que se asociará.

1. (Opcional) Para tener IntelliSense para ptvsd en el equipo local, instale el paquete de ptvsd en su entorno de Python.

1. Seleccione **Depurar > Asociar al proceso**.

1. En el cuadro de diálogo **Asociar al proceso** que aparece, establezca **Tipo de conexión** en **Depuración remota de Python (ptvsd)**. (En versiones anteriores de Visual Studio estas se denominaban **Transporte** y **Depuración remota de Python**).

1. En el campo **Destino de la conexión** (**Calificador** en versiones anteriores), escriba `tcp://<secret>@<ip_address>:5678`, donde `<secret>` es la cadena pasada `enable_attach` en el código Python, `<ip_address>` es la del equipo remoto (que puede ser una dirección explícita o un nombre como myvm.cloudapp.net), y `:5678` es el número de puerto de depuración remota.

    > [!Warning]
    > Si está realizando una conexión a través de una conexión pública a Internet, debería utilizar `tcps` en su lugar y seguir las instrucciones siguientes para la [Protección de la conexión del depurador con SSL](#securing-the-debugger-connection-with-ssl).

1. Presione ENTRAR para rellenar la lista de procesos de ptvsd disponibles en el equipo:

    ![Escribir el destino de la conexión y enumerar procesos](media/remote-debugging-qualifier.png)

    Si inicia otro programa en el equipo remoto después de rellenar esta lista, haga clic en el botón **Actualizar**.

1. Seleccione el proceso para depurar y después haga clic en **Adjuntar**, o haga doble clic en el proceso.

1. Visual Studio cambia después al modo de depuración mientras el script continúa ejecutándose en el equipo remoto, lo que proporciona todas las capacidades normales de [depuración](debugging.md). Por ejemplo, establezca un punto de interrupción en la línea `if guess < number:`, después cambie al equipo remoto y escriba otro intento. Una vez hecho esto, Visual Studio en el equipo local se detiene en ese punto de interrupción, muestra las variables locales, etc.:

    ![Se ha llegado al punto de interrupción](media/remote-debugging-breakpoint-hit.png)

1. Al detener la depuración, Visual Studio se desasocia del programa, que continúa ejecutándose en el equipo remoto. ptvsd también sigue escuchando para adjuntar depuradores, por lo que se puede volver a adjuntar al proceso en cualquier momento.

1. Si se detiene el programa remoto, Visual Studio no desasociará automáticamente el depurador, pero 

### <a name="connection-troubleshooting"></a>Solución de problemas de conexión

1. Asegúrese de que ha seleccionado **Depuración remota de Python (ptvsd)** para el **Tipo de conexión** (**Depuración remota de Python** para **Transporte** con versiones anteriores).
1. Compruebe que el secreto en **Destino de la conexión** (o **Calificador**) coincide exactamente con el secreto en el código remoto.
1. Compruebe que la dirección IP en **Destino de la conexión** (o **Calificador**) coincide exactamente con la del equipo remoto.
1. Compruebe que esté abierto el puerto de depuración remota en el equipo remoto y que ha incluido el sufijo de puerto en el destino de la conexión, por ejemplo `:5678`.
    - Si necesita usar un puerto diferente, puede especificarlo en la llamada a `enable_attach` mediante el argumento `address`, como en `ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))`. En este caso, abra ese puerto concreto en el firewall.
1. Compruebe que la versión de ptvsd instalada en el equipo remoto, tal como la devuelve `pip3 list`, coincide con la que usa la versión de las herramientas de Python que se usa en Visual Studio en la tabla siguiente. Si es necesario, actualice ptvsd en el equipo remoto.

    | Versión de Visual Studio | Versión de las herramientas de Python/ptvsd |
    | --- | --- |
    | 2017 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |


## <a name="securing-the-debugger-connection-with-ssl"></a>Protección de la conexión del depurador con SSL

De forma predeterminada, la conexión al servidor de depuración remota de ptvsd solo está protegida por el secreto y todos los datos se pasan como texto sin formato. Para una conexión más segura, ptvsd es compatible con SSL, que se define como sigue:

1. En el equipo remoto, genere archivos de certificado autofirmado y de clave independientes con openssl:
    
    ```bash
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Cuando se le solicite, use el nombre de host o la dirección IP (lo que use para conectarse) para el **Nombre común** cuando se lo solicite openssl.

    (Vea [Certificados autofirmados](http://docs.python.org/3/library/ssl.html#self-signed-certificates) en la documentación del módulo `ssl` de Python para obtener más detalles. Tenga en cuenta que en esa documentación el comando solo genera un único archivo combinado).

1. En el código, modifique la llamada a `enable_attach` para incluir los argumentos `certfile` y `keyfile` usando los nombres de archivo como valores (estos argumentos tienen el mismo significado que para la función estándar `ssl.wrap_socket` de Python):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```
    
    También puede realizar el mismo cambio en el archivo de código en el equipo local, pero dado que este código no se ejecuta realmente, no es estrictamente necesario.    

1. Reinicie el programa de Python en el equipo remoto, para prepararlo para la depuración.

1. Proteja el canal agregando el certificado a la CA raíz de confianza en el equipo Windows con Visual Studio:

    1. Copie el archivo de certificado desde el equipo remoto al equipo local.
    1. Abra el Panel de Control y vaya a **Herramientas administrativas > Administrar certificados de equipo**.
    1. En la ventana que aparece, expanda **Entidades de certificación raíz de confianza** en el lado izquierdo, haga clic con el botón derecho en **Certificados** y seleccione **Todas las tareas > Importar...**
    1. Vaya al archivo `.cer` copiado desde el equipo remoto, selecciónelo y, después, haga clic en los cuadros de diálogo para completar la importación.

1. Repita el proceso de asociación en Visual Studio como se ha descrito anteriormente y ahora use `tcps://` como protocolo para el **Destino de la conexión** (o **Calificador**).

    ![Selección del transporte de depuración remota con SSL](media/remote-debugging-qualifier-ssl.png)

### <a name="warnings"></a>Advertencias

Visual Studio le avisará sobre posibles problemas de certificado cuando se conecta a través de SSL, como se describe a continuación. Puede ignorar las advertencias y continuar, pero aunque el canal se cifrará contra el espionaje, puede estar abierto a ataques de tipo "Man in the middle".

1. Si ve la siguiente advertencia "El certificado remoto no es de confianza", significa que no ha agregado correctamente el certificado a la CA raíz de confianza. Compruebe esos pasos y vuelve a intentarlo.

    ![Advertencia de confianza de certificado SSL](media/remote-debugging-ssl-warning.png)

1. Si ve la siguiente advertencia "El nombre del certificado remoto no coincide con el nombre de host", significa que no se han usado la dirección IP o el nombre de host correctos como el **Nombre común** al crear el certificado.

    ![Advertencia de nombre de host de certificado SSL](media/remote-debugging-ssl-warning2.png)

> [!Warning]
> En la actualidad, Visual Studio 2017 se bloquea cuando omite estas advertencias. Asegúrese de corregir todos los problemas antes de intentar conectarse.

