---
title: Uso de Visual Studio Tools para Unity | Microsoft Docs
description: Aprenda a usar las características de productividad e integración de Visual Studio Tools para Unity. Use también el depurador de Visual Studio para el desarrollo de Unity.
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 9a89f83ecaa4545eb6151c7a92e76a08708c3855
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341388"
---
# <a name="use-visual-studio-tools-for-unity"></a>Uso de Visual Studio Tools para Unity

En esta sección aprenderá a utilizar las características de productividad e integración de Visual Studio Tools para Unity y cómo utilizar al depurador de Visual Studio para el desarrollo en Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Abrir scripts de Unity en Visual Studio

Una vez que Visual Studio se [establece como el editor externo para Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-to-use-visual-studio), al hacer doble clic en un script del editor de Unity se iniciará automáticamente o se cambiará a Visual Studio y se abrirá el script elegido.

Como alternativa, puede abrir Visual Studio sin ningún script abierto en el editor de código fuente seleccionando el menú **activos > abrir proyecto de C#** en Unity.

:::zone pivot="windows"
![Abrir el proyecto de C# en Visual Studio](../media/vs/vstu-open-csharp-project.png)
:::zone-end
:::zone pivot="macos"
![Abra el proyecto de C# en Visual Studio para Mac](../media/vsm/vstu-open-csharp-project.png)
:::zone-end

## <a name="unity-documentation-access"></a>Acceso a la documentación de Unity

Puede acceder rápidamente a la documentación de creación de scripts de Unity desde Visual Studio. Si Visual Studio Tools para Unity no encuentra localmente la documentación de la API, intentará encontrarla en línea.

:::zone pivot="windows"
- En Visual Studio, resalte o coloque el cursor sobre la API de Unity sobre la que quiere obtener información y, después, presione **Ctrl**+**Alt**+**M** , **Ctrl**+**H**
- También puede usar el menú **ayuda > referencia de API de Unity** en lugar del KeyBinding.
![Menú de referencia de la API de Unity en Visual Studio](../media/vs/help-unity-documentation.png)
:::zone-end
:::zone pivot="macos"
- En Visual Studio para Mac, resalte o coloque el cursor sobre la API de Unity sobre la que desea obtener información y, a continuación, presione **cmd** + **'**
- También puede usar el menú **ayuda > referencia de API de Unity** en lugar del KeyBinding.
![Menú de referencia de la API de Unity en Visual Studio para Mac](../media/vsm/help-unity-documentation.png)
:::zone-end

## <a name="intellisense-for-unity-api-messages"></a>IntelliSense para mensajes de API de Unity

La integridad del código de IntelliSense facilita la implementación de mensajes de la API de Unity en scripts de MonoBehaviour y ayuda a conocer cómo funciona esta API. Para usar IntelliSense para mensajes de Unity:

1. Coloque el cursor en una nueva línea dentro del cuerpo de una clase que se derive de `MonoBehaviour`.

2. Comience a escribir el nombre de un mensaje de Unity, como `OnTriggerEnter`.

3. Una vez que haya escrito las letras " **ontri** ", aparece una lista de sugerencias de IntelliSense.

:::zone pivot="windows"

![Uso de IntelliSense en Visual Studio](../media/vs/intellisense-example.png)  

:::zone-end

4. La selección de la lista se puede cambiar de tres maneras:

    - Con las teclas de flecha **arriba** y **abajo**.

    - Al hacer clic con el mouse en el elemento deseado.

    - Al seguir escribiendo el nombre del elemento deseado.

5. IntelliSense puede insertar el mensaje de Unity seleccionado, incluidos todos los parámetros necesarios:

    - Al presionar **Tab**.

    - Al presionar **Entrar**.

    - Al hacer doble clic en el elemento seleccionado.

:::zone pivot="windows"

![Inserción de mensajes de Unity de IntelliSense en Visual Studio](../media/vs/vstu-intellisense2.png)

:::zone-end

## <a name="unity-monobehavior-scripting-wizard"></a>Asistente de scripting de MonoBehavior de Unity

Puede usar al asistente de MonoBehavior para ver una lista de todos los métodos de API de Unity e implementar rápidamente una definición vacía. Esta característica, especialmente con la opción **Generar comentarios de método** habilitada, es útil si todavía está aprendiendo lo que está disponible en la API de Unity.

Para crear definiciones vacías de método MonoBehavior con el asistente de MonoBehavior, siga estos pasos:

1. En Visual Studio, coloque el cursor donde quiera que se inserten los métodos y, después, presione **Ctrl**+**Mayús**+**M** para iniciar el asistente de MonoBehavior. En Visual Studio para Mac, presione **cmd** + **Shift** + **M**.

2. En la ventana **Crear métodos de script** , marque la casilla junto al nombre de cada método que quiere agregar.

3. Use la lista desplegable **Versión de marco de trabajo** para seleccionar la versión que desee.

4. De forma predeterminada, los métodos se insertan en la posición del cursor. Como alternativa, puede elegir insertarlos después de cualquier método que esté ya implementado en la clase si cambia el valor de la lista desplegable **Punto de inserción** por la ubicación que desee.

5. Si quiere que el asistente genere los comentarios de los métodos que ha seleccionado, marque la casilla **Generar comentarios de métodos**. Estos comentarios están diseñados para ayudarlo a entender cuando se llama al método y cuáles son sus responsabilidades generales.

6. Seleccione el botón **Aceptar** para salir del asistente e insertar los métodos en el código.

:::zone pivot="windows"

![Cuadro de diálogo del asistente de monobehavior en Visual Studio.](../media/vs/vstu-monobehavior-wizard.png)
:::zone-end
:::zone pivot="macos"

![El cuadro de diálogo Asistente de monobehavior en Visual Studio para Mac.](../media/vsm/vstu-monobehavior-wizard.png)
:::zone-end   

## <a name="unity-project-explorer"></a>Explorador de proyectos de Unity
El Explorador de proyectos de Unity muestra todos los archivos de proyecto y directorios de Unity de la misma manera que el Editor de Unity. La experiencia es diferente a navegar por los scripts de Unity con el Explorador de soluciones de Visual Studio normal, que los organiza en proyectos y una solución generada por Visual Studio.

:::zone pivot="windows"
- En el menú principal de Visual Studio, seleccione **Ver > Explorador de proyectos de Unity**. Método abreviado de teclado: **Alt** + **Shift** + **E** 
 ![ ver la ventana Explorador de proyectos de Unity.](../media/vs/unity-project-explorer.png)
:::zone-end
:::zone pivot="macos"
- En Visual Studio para Mac, el Panel de solución se comporta automáticamente de esta manera cuando se abre un proyecto de Unity.
:::zone-end
## <a name="unity-debugging"></a>Depuración de Unity

Visual Studio Tools para Unity permite depurar scripts de editor y juego del proyecto de Unity mediante el potente depurador de Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Depuración en el editor de Unity

#### <a name="start-debugging"></a>Iniciar depuración
:::zone pivot="windows"

1. Conecte Visual Studio a Unity haciendo clic en el botón **Reproducir** llamado **Attach to Unity** (Asociar a Unity), o use el método abreviado de teclado **F5**.
![Haga clic en Reproducir en Visual Studio](../media/vs/vstu-play-button.png)

:::zone-end
:::zone pivot="macos"

1. Conecte Visual Studio a Unity al hacer clic en el botón **Reproducir** o escriba **Comando + Entrar** o **F5**.
![Haga clic en reproducir en Visual Studio para Mac](../media/vsm/using-vsmac-tools-unity-image5.png)

:::zone-end

2. Vaya a Unity y haga clic en el botón **Reproducir** para ejecutar el juego en el editor.
:::zone pivot="windows"
![Haga clic en reproducir en Unity en Windows](../media/vs/vstu-unity-play-button.png)
:::zone-end
:::zone pivot="macos"
![Haga clic en reproducir en Unity en macOS](../media/vsm/using-vsmac-tools-unity-image6.png)
:::zone-end

3. Cuando se ejecuta el juego en el editor de Unity mientras se está conectado a Visual Studio, cualquier punto de interrupción detectado detiene la ejecución del juego y muestra la línea de código donde el juego alcanza el punto de interrupción en Visual Studio.

#### <a name="stop-debugging"></a>Detener depuración

:::zone pivot="windows"

Haga clic en el botón **Detener** en Visual Studio o use el método abreviado de teclado **MAYÚS+F5**.
![Haga clic en Detener en Visual Studio](../media/vs/vstu-stop-debugger.png)

:::zone-end
:::zone pivot="macos"

Haga clic en el botón **Detener** de Visual Studio para Mac o presione **Mayús + Comando + Entrar**.
![Haga clic en detener en Visual Studio para Mac](../media/vsm/using-vsmac-tools-unity-image7.png)

:::zone-end

Para más información sobre la depuración en Visual Studio, consulte [Primer vistazo al depurador de Visual Studio](/debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Asociar a Unity y reproducir

Para mayor comodidad, puede cambiar el botón **Attach to Unity** (Asociar a Unity) al modo **Attach to Unity and Play** (Asociar a Unity y reproducir).

:::zone pivot="windows"

1. Haga clic en la pequeña **flecha abajo** junto al botón **Attach to Unity** (Asociar a Unity).
2. Seleccione **Attach to Unity and Play** (Asociar a Unity y reproducir) en el menú desplegable.
   ![Adjuntar y reproducir en Visual Studio](../media/vs/vstu-attach-and-play.png)

El botón Reproducir pasa a llamarse **Attach to Unity and Play** (Asociar a Unity y reproducir). Al hacer clic en este botón o usar el método abreviado de teclado **F5** ahora se cambia automáticamente al editor de Unity y se ejecuta el juego en el editor; también se asocia el depurador de Visual Studio.

:::zone-end
:::zone pivot="macos"
El inicio de la depuración y la reproducción del editor Unity se pueden llevar a cabo en un solo paso directamente desde Visual Studio para Mac eligiendo la configuración **Asociar a Unity y jugar**.

![Seleccione asociar a Unity y reproducir en Visual Studio para Mac](../media/vsm/using-vsmac-tools-unity-image8.png)
:::zone-end

> [!NOTE]
> Si inició la depuración con la configuración de **adjuntar a Unity y reproducir** , el botón **detener** también detendrá el editor de Unity.

### <a name="debug-unity-player-builds"></a>Depuración de las compilaciones del reproductor de Unity

Puede depurar las compilaciones de desarrollo de reproductores de Unity con Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Habilitación de la depuración de scripts en un reproductor de Unity

1. En Unity, seleccione **File > Build Settings** (Archivo > Configuración de compilación) para abrir la configuración de compilación.
2. En la ventana de configuración de compilación, marque las casillas **Development Build** (Compilación de desarrollo) y **Script Debugging** (Depuración de scripts).

   ![Establezca la configuración de compilación de Unity para la depuración.](../media/vs/vstu-debugging-build-settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Selección de una instancia de Unity a la que asociar el depurador

:::zone pivot="windows"

- En el menú principal de Visual Studio, elija **Depurar > Asociar depurador de Unity**.

   ![Asocie el depurador de Unity.](../media/vs/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")

   En el cuadro de diálogo **Seleccionar instancia de Unity** se muestra información sobre cada instancia de Unity a la que puede conectarse.

   ![Elija una instancia de Unity a la que conectarse.](../media/vs/vstu-attach-debugger.png "vstu_connection_to_unity")

   **Proyecto**

   El nombre del proyecto de Unity que se está ejecutando en esta instancia de Unity.

   **Equipo** Nombre del equipo o dispositivo en el que se está ejecutando esta instancia de Unity.

   **Tipo** **Editor** si esta instancia de Unity se está ejecutando como parte del Editor de Unity; **Reproductor** si esta instancia de Unity es un reproductor independiente.

   **Puerto** Número de puerto del socket UDP a través del que se está comunicando esta instancia de Unity.

> [!IMPORTANT]
> Dado que Visual Studio Tools para Unity y la instancia de Unity se comunican a través de un socket de red UDP, el Firewall puede necesitar regla para permitirlo. Si es necesario, es posible que vea un símbolo del sistema, tendrá que autorizar la conexión para que VSTU y Unity puedan comunicarse.

:::zone-end
:::zone pivot="macos"

- En Visual Studio para Mac, en el menú superior, elija **ejecutar > asociar al proceso**. 
- En el cuadro de diálogo **asociar al proceso** , seleccione la opción **depurador de Unity** en el menú desplegable del depurador en la parte inferior.
- Seleccione una instancia de Unity en la lista y haga clic en el botón **adjuntar** .

:::zone-end

### <a name="debug-a-dll-in-your-unity-project"></a>Depurar un archivo DLL en un proyecto de Unity

Muchos desarrolladores de Unity están escribiendo componentes de código como archivos DLL externos para que la funcionalidad que desarrollan pueda compartirse fácilmente con otros proyectos. Visual Studio Tools para Unity facilita la depuración sin problemas del código de estos archivos DLL con otro código de su proyecto de Unity.

> [!NOTE]
> En este momento, Visual Studio Tools para Unity solo admite archivos DLL administrados. No admite la depuración de archivos DLL de código nativo, como los escritos en C++.

Tenga en cuenta que el escenario descrito aquí supone que tiene el código fuente, es decir, que está desarrollando o reutilizando su propio código o que tiene el código fuente de una biblioteca de terceros y planea implementarlo en su proyecto de Unity como un archivo DLL. Este escenario no describe la depuración de un archivo DLL del que usted no dispone el código fuente.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Para depurar un proyecto de archivo DLL administrado utilizado en su proyecto de Unity

1. Agregue su proyecto DLL existente a la solución de Visual Studio generada por Visual Studio Tools para Unity. Con menor frecuencia, puede que inicie un nuevo proyecto DLL administrado para que contenga componentes de código en su proyecto de Unity. De ser así, puede agregar un nuevo proyecto DLL administrado a la solución de Visual Studio en su lugar.

   ![Agregar el proyecto DLL existente a la solución.](../media/vs/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")

   En ambos casos, Visual Studio Tools para Unity mantiene la referencia del proyecto, aunque tenga que volver a generar los archivos de proyecto y solución, para que solo tenga que realizar estos pasos una vez.

2. Haga referencia al perfil de .NET Framework de Unity correcto en el proyecto DLL. En Visual Studio, en las propiedades del proyecto DLL, establezca la propiedad **Framework de destino** en la versión de .NET Framework de Unity que esté usando. Esta es la Biblioteca de clases base de Unity que coincide con la compatibilidad con la API que su proyecto tiene definido como destino, como las bibliotecas de clases base completas, micro o web de Unity. Esto impide que el archivo DLL llame a métodos de .NET Framework que existan en otros niveles de compatibilidad o marcos de trabajo, pero que podrían no existir en la versión de .NET Framework de Unity que esté utilizando.

> [!NOTE]
> Lo siguiente solo es necesario si usa el entorno de ejecución heredado de Unity. Si usa el nuevo entorno de ejecución de Unity, ya no necesita usar los perfiles 3.5 dedicados. Use un perfil .NET 4.x compatible con su versión de Unity.

   ![Establezca como plataforma de destino de DLL la plataforma Unity.](../media/vs/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")

3. Copie el archivo DLL en la carpeta Activos del proyecto de Unity. En Unity, son activos los archivos que se empaquetan e implementan junto con la aplicación de Unity para que se puedan cargar en tiempo de ejecución. Puesto que los archivos DLL se vinculan en tiempo de ejecución, se deben implementar como recursos. Para que los archivos DLL se implementen como activos, el Editor de Unity necesita que se coloquen en la carpeta Activos del proyecto Unity. Puede hacer esto de dos formas:

   - Modificar la configuración de compilación del proyecto DLL para que incluya una tarea integrada a posteriori que copie los archivos DLL y PDB de salida de la carpeta de salida en la carpeta **Activos** del proyecto de Unity.

   - Modificar la configuración de compilación del proyecto DLL para establecer la carpeta de salida como la carpeta **Activos** del proyecto de Unity. Tanto los archivos DLL como PDB se colocarán en la carpeta **Activos**.

   Los archivos PDB son necesarios para la depuración porque contienen símbolos de depuración de los archivos DLL y asignan el código del archivo DLL a su forma de código fuente. Si tiene como destino el entorno de ejecución heredado, Visual Studio Tools para Unity usará información de los archivos DLL y PDB para crear un archivo DLL.MDB, que es el formato de símbolo de depuración utilizado por el motor de scripting heredado de Unity. Si tiene como destino el entorno de ejecución nuevo y usa archivos PDB portátiles, Visual Studio Tools para Unity no intentará realizar ninguna conversión de símbolo, porque el entorno de ejecución de Unity nuevo puede consumir archivos PDB portátiles de manera nativa.

   Puede encontrar más información sobre la generación de PDB [aquí](/debugger/how-to-set-debug-and-release-configurations.md). Si tiene como destino el entorno de ejecución nuevo, asegúrese de que la opción "Información de depuración" esté establecida en "Portátil" para así generar de manera adecuada archivos PDB portátiles. Si tiene como destino el entorno de ejecución heredado, debe usar "Full" (Completo).

4. Depure el código que ha creado. Ahora puede depurar el código fuente de archivos DLL junto con el código fuente del proyecto de Unity y utilizar todas las características de depuración a las que está acostumbrado, como los puntos de interrupción y ejecutar código paso a paso.

## <a name="keyboard-shortcuts"></a>Métodos abreviados de teclado

Puede acceder rápidamente a las herramientas de Unity para la funcionalidad de Visual Studio mediante el uso de los métodos abreviados de teclado. Este es un resumen de los métodos abreviados disponibles.

:::zone pivot="windows"

|Comando|Acceso directo|Nombre de comando de acceso directo|
|-------------|--------------|---------------------------|
|Abrir el asistente de MonoBehavior|**Ctrl**+**Mayús**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Abrir el Explorador de proyectos de Unity|**Alt**+**Mayús**+**E**|**View.UnityProjectExplorer**|
|Acceder a la documentación de Unity|**Ctrl**+**Alt**+**M, Ctrl**+**H**|**Help.UnityAPIReference**|
|Adjuntar a depurador de Unity (reproductor o editor)|**_sin valor predeterminado_**|**Debug.AttachUnityDebugger**|

Si no le gusta el valor predeterminado, puede cambiar las combinaciones de teclas de método abreviado. Para obtener información sobre cómo cambiarlo, vea [Identificar y personalizar métodos abreviados de teclado en Visual Studio](/docs/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

:::zone-end
:::zone pivot="macos"

|Comando|Acceso directo|Nombre de comando de acceso directo|
|-------------|--------------|---------------------------|
|Abrir el asistente de MonoBehavior|**Cmd** + **Desplazamiento** + **M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Acceder a la documentación de Unity|**Cmd + '**|**Help.UnityAPIReference**|

Si no le gusta el valor predeterminado, puede cambiar las combinaciones de teclas de método abreviado. Para obtener información sobre cómo cambiarlo, vea [personalizar el IDE](/mac/customizing-the-ide#key-bingings).

:::zone-end
