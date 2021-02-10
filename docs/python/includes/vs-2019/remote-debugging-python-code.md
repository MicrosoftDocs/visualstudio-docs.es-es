---
title: Depuración de código de Python en equipos Linux remotos
description: Use Visual Studio para depurar código de Python que se ejecute en equipos remotos de Linux, incluidos los pasos de configuración necesarios, la seguridad y la solución de problemas.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: dcc5d9746a556af54ea206528fcb9a402e25d700
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916587"
---
En Visual Studio se pueden iniciar y depurar aplicaciones de Python de manera local y remota en un equipo Windows (vea [Depuración remota](../../../debugger/remote-debugging.md)). También puede realizar la depuración remota en un sistema operativo, un dispositivo o una implementación de Python diferentes a CPython mediante la [biblioteca debugpy](https://pypi.org/project/debugpy/).

Al usar debugpy, el código de Python que se depura hospeda el servidor de depuración al que puede asociar Visual Studio. El hospedaje necesita una pequeña modificación en el código para importar y habilitar al servidor. Además, es posible que haya que modificar la configuración de la red o del firewall en el equipo remoto para permitir conexiones TCP.

> [!NOTE]
> En Visual Studio 2019 16.4 y versiones anteriores, se usó la [biblioteca ptvsd](https://pypi.python.org/pypi/ptvsd). La biblioteca debugpy reemplazó a ptvsd 4 en Visual Studio 2019 16.5.

## <a name="set-up-a-linux-computer"></a>Configurar un equipo Linux

Los elementos siguientes son necesarios para seguir este tutorial:

- Un equipo remoto que ejecute Python en un sistema operativo como Mac OSX o Linux.
- El puerto 5678 (entrada) abierto en el firewall de ese equipo, que es el valor predeterminado para la depuración remota.

> [!NOTE]
> Este tutorial se basa en Visual Studio 2019 16.6.

Puede crear fácilmente una [máquina virtual de Linux en Azure](/azure/virtual-machines/linux/creation-choices) y [acceder mediante Escritorio remoto](/azure/virtual-machines/linux/use-remote-desktop) desde Windows. Ubuntu para la máquina virtual resulta útil porque Python está instalado de forma predeterminada; de lo contrario, vea la lista de [Instalación de los intérpretes de Python](../../installing-python-interpreters.md) para obtener otras ubicaciones de descarga de Python.

Para obtener detalles sobre cómo crear una regla de firewall para una máquina virtual de Azure, vea [Apertura de puertos en una máquina virtual con Azure Portal](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Preparar el script para la depuración

1. En el equipo remoto, cree un archivo de Python denominado *guessing-game.py* con el código siguiente:

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

1. Instale el paquete `debugpy` en su entorno mediante `pip3 install debugpy`.
   >[!NOTE]
   >Es buena idea registrar la versión de debugpy que se instala en caso de necesitarla para solucionar problemas; la [lista de debugpy](https://pypi.org/project/debugpy/) también muestra las versiones disponibles.

1. Habilite la depuración remota al agregar el código siguiente al primer punto posible de *guessing-game.py*, delante de otro código. (Aunque no es un requisito estricto, es imposible depurar subprocesos en segundo plano generados antes de la llamada a la función `listen`).

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. Guarde el archivo y ejecute `python3 guessing-game.py`. La llamada a `listen` se ejecuta en segundo plano y espera las conexiones entrantes mientras se interactúa con el programa. Si lo desea, se puede llamar a la función `wait_for_client` después de `listen` para bloquear el programa hasta que se asocie el depurador.

> [!Tip]
> Además de `listen` y `wait_for_client`, debugpy también proporciona una función del asistente `breakpoint`, que actúa como un punto de interrupción de programación si el depurador está asociado. También hay una función `is_client_connected` que devuelve `True` si el depurador está asociado (tenga en cuenta que no es necesario comprobar este resultado antes de llamar a cualquier otra función `debugpy`).

## <a name="attach-remotely-from-python-tools"></a>Asociar desde Herramientas de Python de forma remota

En estos pasos, estableceremos un punto de interrupción simple para detener el proceso remoto.

1. Cree una copia del archivo remoto en el equipo local y ábralo en Visual Studio. No importa dónde se encuentre el archivo, pero su nombre debe coincidir con el nombre del script en el equipo remoto.

1. (Opcional) Para tener IntelliSense para debugpy en el equipo local, instale el paquete de debugpy en su entorno de Python.

1. Seleccione **Depurar** > **Asociar al proceso**.

1. En el cuadro de diálogo **Asociar al proceso** que aparece, establezca **Tipo de conexión** en **Depuración remota de Python (debugpy)** .

1. En el campo **Destino de la conexión**, escriba `tcp://<ip_address>:5678`, donde `<ip_address>` es la del equipo remoto (que puede ser una dirección explícita o un nombre como myvm.cloudapp.net), y `:5678` es el número de puerto de depuración remota.

1. Presione **Entrar** para rellenar la lista de procesos de debugpy disponibles en el equipo:

    ![Escribir el destino de la conexión y enumerar procesos](../../media/remote-debugging-attach.png)

    Si inicia otro programa en el equipo remoto después de rellenar esta lista, haga clic en el botón **Actualizar**.

1. Seleccione el proceso para depurar y después haga clic en **Adjuntar**, o haga doble clic en el proceso.

1. Visual Studio cambia después al modo de depuración mientras el script continúa ejecutándose en el equipo remoto, lo que proporciona todas las capacidades normales de [depuración](../../debugging-python-in-visual-studio.md). Por ejemplo, establezca un punto de interrupción en la línea `if guess < number:`, después cambie al equipo remoto y escriba otro intento. Una vez hecho esto, el programa Visual Studio del equipo local se detiene en ese punto de interrupción, muestra las variables locales, etc.:

    ![Visual Studio detiene la depuración cuando se alcanza el punto de interrupción](../../media/remote-debugging-breakpoint-hit.png)

1. Al detener la depuración, Visual Studio se desconecta del programa, que continúa ejecutándose en el equipo remoto. debugpy también sigue escuchando para conectar depuradores, por lo que se puede volver a conectar al proceso en cualquier momento.

### <a name="connection-troubleshooting"></a>Solución de problemas de conexión

1. Asegúrese de haber seleccionado **Remota de Python (debugpy)** para **Tipo de conexión**
1. Compruebe que el secreto en **Destino de la conexión** coincide exactamente con el secreto en el código remoto.
1. Compruebe que la dirección IP en **Destino de la conexión** coincide exactamente con la del equipo remoto.
1. Compruebe que ha abierto el puerto de depuración remota en el equipo remoto y que ha incluido el sufijo de puerto en el destino de la conexión, por ejemplo `:5678`.
    - Si necesita usar un puerto diferente, puede especificarlo en `listen`, como en `debugpy.listen((host, port))`. En este caso, abra ese puerto concreto en el firewall.
1. Compruebe que la versión de debugpy instalada en el equipo remoto, tal como la devuelve `pip3 list`, coincide con la que usa la versión de las herramientas de Python que se usa en Visual Studio en la tabla siguiente. Si es necesario, actualice debugpy en el equipo remoto.

    | Versión de Visual Studio | Versión de debugpy o de las herramientas de Python |
    | --- | --- |
    | 2019 16.6 | 1.0.0b5 |
    | 2019 16.5 | 1.0.0b1 |

> [!NOTE]
> Las versiones de Visual Studio 2019 16.0 a 16.4 usaban ptvsd, no debugpy. El proceso de este tutorial para esas versiones es similar, pero los nombres de función son diferentes. Visual Studio 2019 16.5 usa debugpy, pero los nombres de función eran los mismos que los de ptvsd. En lugar de `listen`, usaría `enable_attach`. En lugar de `wait_for_client`, usaría `wait_for_attach`. En lugar de `breakpoint`, usaría `break_into_debugger`.

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>Uso de ptvsd 3.x para la depuración heredada
Visual Studio 2017 15.8 y versiones posteriores usan un depurador basado en ptvsd 4.1+. Visual Studio 2019 16.5 y las versiones posteriores usan un depurador basado en debugpy. Estas versiones del depurador son compatibles con Python 2.7 y Python 3.5+. Si usa Python 2.6, 3.1 hasta 3.4 o IronPython, Visual Studio muestra el error **El depurador no admite este entorno de Python**. La siguiente información solo se aplica a la depuración remota con ptvsd 3.x.

1. Con ptvsd 3.x, la función `enable_attach` que requiere que pase un "secreto" como el primer argumento que restringe el acceso al script en ejecución. Este secreto se escribe cuando se adjunta el depurador remoto. Aunque no se recomienda, puede permitir que cualquiera se conecte, mediante `enable_attach(secret=None)`.

1. La dirección URL de destino de conexión es `tcp://<secret>@<ip_address>:5678`, donde `<secret>` es la cadena `enable_attach` que se pasa en el código de Python.

De forma predeterminada, la conexión al servidor de depuración remota de ptvsd 3.x solo está protegida por el secreto y todos los datos se pasan como texto sin formato. Para una conexión más segura, ptvsd 3.x admite SSL con el protocolo `tcsp`, que se configura de la siguiente manera:

1. En el equipo remoto, genere archivos de certificado autofirmado y de clave independientes con openssl:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Cuando se le solicite, use el nombre de host o la dirección IP (lo que use para conectarse) para el **Nombre común** cuando se lo solicite openssl.

    (Vea [Certificados autofirmados](https://docs.python.org/3/library/ssl.html#self-signed-certificates) en la documentación del módulo `ssl` de Python para obtener más detalles. Tenga en cuenta que en esa documentación el comando solo genera un único archivo combinado).

1. En el código, modifique la llamada a `enable_attach` para incluir los argumentos `certfile` y `keyfile` usando los nombres de archivo como valores (estos argumentos tienen el mismo significado que para la función estándar `ssl.wrap_socket` de Python):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    También puede realizar el mismo cambio en el archivo de código en el equipo local, pero dado que este código no se ejecuta realmente, no es estrictamente necesario.

1. Reinicie el programa de Python en el equipo remoto, para prepararlo para la depuración.

1. Proteja el canal agregando el certificado a la CA raíz de confianza en el equipo Windows con Visual Studio:

    1. Copie el archivo de certificado desde el equipo remoto al equipo local.
    1. Abra el **Panel de Control** y vaya a **Herramientas administrativas** > **Administrar certificados de equipo**.
    1. En la ventana que aparece, expanda **Entidades de certificación raíz de confianza** en el lado izquierdo, haga clic con el botón derecho en **Certificados** y seleccione **Todas las tareas** > **Importar**.
    1. Vaya al archivo *.cer* copiado desde el equipo remoto, selecciónelo y, después, haga clic en los cuadros de diálogo para completar la importación.

1. Repita el proceso de asociación en Visual Studio como se ha descrito anteriormente y ahora use `tcps://` como protocolo para el **Destino de la conexión** (o **Calificador**).

    ![Selección del transporte de depuración remota con SSL](../../media/remote-debugging-qualifier-ssl.png)

1. Visual Studio le avisará sobre posibles problemas de certificado cuando se conecta a través de SSL. Puede pasar por alto las advertencias y continuar, pero aunque el canal sigue cifrado frente a la intercepción, puede estar abierto a ataques de tipo "Man in the middle".

    1. Si ve la siguiente advertencia **El certificado remoto no es de confianza**, significa que no ha agregado correctamente el certificado a la CA raíz de confianza. Compruebe esos pasos y vuelve a intentarlo.

        ![Advertencia de confianza de certificado SSL](../../media/remote-debugging-ssl-warning.png)

    1. Si ve la siguiente advertencia **El nombre del certificado remoto no coincide con el nombre de host**, significa que no se han usado la dirección IP o el nombre de host correctos como **Nombre común** al crear el certificado.

        ![Advertencia de nombre de host de certificado SSL](../../media/remote-debugging-ssl-warning2.png)
