---
title: Introducción a crear juegos con Unity en Visual Studio para Mac
description: Introducción a Unity y Visual Studio para Mac
author: asb3993
ms.author: amburns
ms.date: 05/20/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: 8f14d21468336dba220a76ad8978f136d50f96f1
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836164"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Introducción a crear juegos con Unity en Visual Studio para Mac 

Unity es un motor de juego que le permite desarrollar juegos en C#. En este tutorial se muestra cómo empezar a desarrollar y depuración juegos Unity con Visual Studio para Mac y Visual Studio para Mac Tools para la extensión de Unity junto con el entorno de Unity.

Visual Studio para Mac Tools para Unity es una extensión gratuita, instalada con Visual Studio para Mac. Permite a los desarrolladores de Unity aprovechar las ventajas de las características de productividad de Visual Studio para Mac, incluida la excelente compatibilidad de IntelliSense, depuración de las características y mucho más.

## <a name="objectives"></a>Objetivos

> [!div class="checklist"]
> * Obtenga información sobre el desarrollo de Unity con Visual Studio para Mac

## <a name="prerequisites"></a>Requisitos previos

- Visual Studio para Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition o superior ([https://store.unity.com](https://store.unity.com/), requiere una cuenta de unity.com para ejecutarse)

## <a name="intended-audience"></a>Público destinatario

Esta práctica está destinada a desarrolladores que están familiarizados con C#, aunque no se requiere la vasta experiencia.

## <a name="task-1-creating-a-basic-unity-project"></a>Tarea 1: Crear un proyecto básico de Unity

1. Iniciar **Unity**. Si se solicita, inicie sesión.

2. Haga clic en **nuevo**.

    ![Botón de nueva en unity](media/unity-image1.png)

3. Establecer el **nombre del proyecto** a **"UnityLab"** y seleccione **3D**. Haga clic en **crear un proyecto**.

    ![Crear nueva pantalla de proyecto](media/unity-image2.png)

4. Ahora está buscando en la interfaz de Unity de forma predeterminada. Tiene la jerarquía de la escena con objetos del juego en el lado izquierdo, una vista 3D de la escena en blanco, que se muestra en la parte central, un panel de archivos de proyecto en la parte inferior y el inspector y los servicios de la derecha. Por supuesto, hay mucho más que eso, pero estos son algunos de los componentes más importantes.

    ![interfaz de unity en blanco](media/unity-image3.png)

5. Para desarrolladores nuevos en Unity, todo lo que se ejecuta en la aplicación existirá en el contexto de un **escena**. Un archivo de escena es un único archivo que contiene a todo tipo de metadatos sobre los recursos utilizados en el proyecto de la escena actual y sus propiedades. Al empaquetar la aplicación para una plataforma, finalizará la aplicación resultante es una colección de uno o más escenas, además de cualquier código dependiente de la plataforma que agregue. Puede tener tantas escenas como quiera en un proyecto.

6. La nueva escena solo tiene una cámara y una luz direccional. Una escena requiere un **cámara** para cualquier elemento sea visible y un **Audio Listener** para cualquier elemento audibles. Estos componentes están conectados a un **GameObject**.

7. Seleccione el **cámara principal** objeto desde el **jerarquía** panel.

    ![objeto de cámara principal resaltado en el panel de jerarquías](media/unity-image4.png)

8. Seleccione el **Inspector** panel desde el lado derecho de la ventana para revisar sus propiedades. Propiedades de la cámara incluyen información de transformación, en segundo plano, tipo de proyección, campo de visión y así sucesivamente. También se agregó un componente Audio Listener de forma predeterminada, que esencialmente hace audio de la escena de un micrófono virtual conectado a la cámara.

    ![panel del inspector](media/unity-image5.png)

9. Seleccione el **luz direccional** objeto. Esto proporciona a luz a la escena para que los componentes, como los sombreadores sepan cómo procesar los objetos.

    ![objeto light dirección resaltado](media/unity-image6.png)

10. Use la **Inspector** para ver que incluye propiedades comunes de iluminación como tipo, color, intensidad, tipo de instantánea y así sucesivamente.

    ![Examinar las propiedades en el panel del inspector](media/unity-image7.png)

11. Es importante hacer notar que los proyectos de Unity son un poco diferentes de su Visual Studio para homólogos de Mac. En el **proyecto** pestaña en la parte inferior, haga clic en el **activos** carpeta y seleccione **mostrar en Finder**.

    ![mostrar en la acción de contexto de finder](media/unity-image8.png)

12. Los proyectos contienen **activos**, **biblioteca**, **ProjectSettings**, y **Temp** pueden ver las carpetas que usted. Sin embargo, es el único que se muestra en la interfaz de la **activos** carpeta. El **biblioteca** carpeta es la memoria caché local para los activos importados; mantiene todos los metadatos para los recursos. El **ProjectSettings** , puede configurar almacenes de carpetas. El **Temp** carpeta se utiliza para los archivos temporales de Mono y Unity durante el proceso de compilación. También hay un archivo de solución que se puede abrir en Visual Studio para Mac (**UnityLab.sln** aquí).

    ![activos en el finder](media/unity-image9.png)

13. Cerrar la **buscador** ventana y volver a **Unity**.

14. El **activos** carpeta contiene todos los activos de arte, código, audio, etcetera. Ahora está vacío, pero todos los archivos que se incluya en su proyecto va aquí. Esto siempre es la carpeta de nivel superior en el **Editor de Unity**. Pero siempre agregar y quitar archivos a través de la interfaz de Unity (o Visual Studio para Mac) y nunca a través del sistema de archivos directamente.

    ![carpeta de activos de unity](media/unity-image10.png)

15. El **GameObject** es fundamental para el desarrollo de Unity casi todo lo que se derive de ese tipo, incluidos los modelos, las luces, sistemas de partículas y así sucesivamente. Agregue un nuevo **cubo** objeto a la escena a través de la **GameObject > objeto 3D > cubo** menú.

    ![objeto de cubo en la escena](media/unity-image11.png)

16. Eche un vistazo rápido a las propiedades del nuevo **GameObject** y verá que tiene un nombre, etiqueta, layer y transformación. Estas propiedades son comunes a todos los **GameObjects**. Además, varios componentes se asociaron a la **cubo** para proporcionar necesitan funcionalidad incluidos malla filtro, colisionador de cuadro y representador.

    ![propiedades de objeto de juego](media/unity-image12.png)

17. Cambiar el nombre de la **cubo** objeto, que tiene el nombre **"Cubo"** de forma predeterminada, para **"Enemigo"** . Asegúrese de que presionar **ENTRAR** para guardar el cambio. Este será el cubo enemigo en nuestro juego sencillo.

    ![propiedad de cambio de nombre de objeto de cubo](media/unity-image13.png)

18. Agregue otro **cubo** objeto a la escena utilizando el mismo proceso que anteriormente y el nombre de éste **"Player"** .

    ![cambiar el nombre del segundo objeto de cubo](media/unity-image14.png)

19. Etiquetar el objeto player **"Player"** también (consulte **etiqueta** control de lista desplegable solo en el campo nombre). Vamos a usar en el script enemigo para ayudar a localizar el objeto de juego del Reproductor.

    ![el objeto player de etiquetado](media/unity-image15.png)

20. En el **escena** ver, mover el objeto player fuera del objeto enemigo a lo largo del eje Z con el mouse. Puede mover a lo largo del eje Z, seleccione y arrastre el cubo por su **rojo** panel hacia la **azul** línea. Puesto que el cubo se encuentra en el espacio 3D, pero solo se puede arrastrar en 2D cada vez, el eje en el que se arrastra es especialmente importante.

    ![cubo de que muestra la vista de escena](media/unity-image16.png)

21. Mueva el cubo hacia abajo y hacia la derecha en el eje. Esto actualiza la **Transform.Position** propiedad en el **Inspector**. Asegúrese de arrastrar a una ubicación de forma similar a los que se muestran aquí para facilitar los pasos posteriores en el laboratorio.

    ![mover un cubo a lo largo del eje](media/unity-image17.png)

22. Ahora puede agregar código para controlar la lógica de enemigos para que persigue el Reproductor. Haga clic en el **activos** carpeta en el **proyecto** rellenar y seleccione **crear > C# Script**.

    ![C#acción de contexto de script](media/unity-image18.png)

23. El nombre del nuevo C# script **"EnemyAI"** .

    ![Script de C#](media/unity-image19.png)

24. Para adjuntar scripts a objetos de juego arrastrar el script recién creado en el **enemigo** objeto en el **jerarquía** panel. Ahora, ese objeto usará los comportamientos de esta secuencia de comandos.

    ![resaltado que muestra el script agrega al objeto de juego](media/unity-image20.png)

25. Seleccione **archivo > Guardar escenas** para guardar la escena actual. Asígnele el nombre **"MyScene"** .

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Tarea 2: Trabajar con Visual Studio for Mac Tools para Unity

1. La mejor forma de editar C# código consiste en usar Visual Studio para Mac. Puede configurar Unity para usar Visual Studio para Mac como su controlador predeterminado. Seleccione **Unity > Preferencias**.

2. Seleccione el **herramientas externas** ficha. Desde el **External Script Editor** lista desplegable, seleccione **examinar** y seleccione **aplicaciones/Visual Studio.app**. Como alternativa, si ya existe un **Visual Studio** opción, que seleccione.

    ![pestaña herramientas externas en las preferencias](media/unity-image21.png)

3. Unity está ahora configurado para usar **Visual Studio para Mac** para editar scripts. Cerrar la **preferencias de Unity** cuadro de diálogo.

    ![Visual Studio seleccionada en las preferencias](media/unity-image22.png)

4. Haga doble clic en **EnemyAI.cs** para abrirlo en **Visual Studio para Mac**.

    ![Enemigo activo seleccionado en unity](media/unity-image23.png)

5. La solución de Visual Studio es sencilla. Contiene un **activos** carpeta (el mismo desde **buscador**) y el **EnemyAI.cs** script que creó anteriormente. En proyectos más sofisticados, probablemente será diferente del que se ve en Unity la jerarquía.

    ![Panel de solución de Visual Studio para Mac](media/unity-image24.png)

6. **EnemyAI.cs** está abierto en el editor. El script inicial solo contiene códigos auxiliares para el **iniciar** y **actualización** métodos.

7. Reemplace el código enemigo inicial con el código siguiente.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;
        
        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. Eche un vistazo rápido en el comportamiento de enemigos simple que se define aquí. En el **iniciar** método, obtenemos una referencia al objeto player (por su etiqueta), así como su **transformar**. En el **actualización** método, que se llama a cada fotograma, el enemigo se moverá hacia el objeto player. Las palabras clave y los nombres de utilizan la codificación en colores para que resulte más fácil entender el código base en Visual Studio para Mac.

9. Guarde los cambios en la secuencia de comandos enemigo en **Visual Studio para Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Tarea 3: Depuración del proyecto de Unity

1. Establezca un punto de interrupción en la primera línea de código en el **iniciar** método. Puede hacer clic en el margen del editor en el cursor de línea o en lugar de destino en la línea y presione **F9**.

    ![Establecer punto de interrupción en visual studio para mac](media/unity-image25.png)

2. Haga clic en el **Iniciar depuración** o presionen **F5**. Esto compilará el proyecto y adjuntar a Unity para la depuración.

    ![botón de inicio en visual studio para mac](media/unity-image26.png)

3. Vuelva a **Unity** y haga clic en el **ejecutar** botón para iniciar el juego.

    ![botón de ejecución de unity](media/unity-image27.png)

4. Se alcanzará el punto de interrupción y ahora puede usar Visual Studio para las herramientas de depuración de Mac.

    ![punto de interrupción en visual studio para mac](media/unity-image28.png)

5. Desde el **variables locales** rellenar, busque el **esto** puntero, que hace referencia a un **EnemyAI** objeto. Expanda la referencia y vea que puede examinar los miembros asociados como **velocidad**.

    ![variables locales de depuración del panel de visual studio para mac](media/unity-image29.png)

6. Quitar el punto de interrupción desde el **iniciar** método del mismo modo que fue agregado por haciendo clic en él en el margen o seleccionar la línea y presione **F9**.

    ![punto de interrupción en visual studio para mac](media/unity-image30.png)

7. Presione **F10** al paso a través de la primera línea de código que busca el **Reproductor** objeto de juego con una etiqueta como parámetro.

8. Mantenga el cursor del mouse sobre el **Reproductor** variable dentro de la ventana del editor de código para ver sus miembros asociados. Incluso puede expandir la superposición para ver las propiedades secundarias.

    ![ventana de depuración en visual studio para el editor de mac](media/unity-image31.png)

9. Presione **F5** o presione la **ejecutar** botón para continuar la ejecución. Volver a Unity para ver el cubo enemigo repetidamente enfocar el cubo del Reproductor. Es posible que deba ajustar la cámara si no está visible.

    ![escena reproducir en unity](media/unity-image32.png)

10. Volver a **Visual Studio para Mac** y establezca un punto de interrupción en la primera línea de la **actualización** método. Se debe alcanzar inmediatamente.

    ![establecer un punto de interrupción en visual studio para mac](media/unity-image33.png)

11. Supongamos que la velocidad es demasiado rápida y va a probar el impacto del cambio sin tener que reiniciar la aplicación. Busque el **velocidad** variable dentro de la **automático** o **variables locales** ventana y, a continuación, cámbielo a **"10"** y presione **ENTRAR** .

    ![ajuste de las variables en la ventana variables locales](media/unity-image34.png)

12. Quitar el punto de interrupción y presione **F5** para reanudar la ejecución.

13. Vuelva a **Unity** para ver la aplicación en ejecución. El cubo enemigo se traslada a una quinta parte de la velocidad original.

    ![ventana de Unity con la ejecución de aplicación](media/unity-image35.png)

14. Detener la aplicación de Unity al hacer clic en el **reproducir** nuevamente en el botón.

    ![detener la aplicación de unity](media/unity-image36.png)

15. Vuelva a **Visual Studio para Mac**. Detener la sesión de depuración, haga clic en el **detener** botón.

    ![Deteniendo la sesión de depuración en Visual Studio para Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Tarea 4: Explorar las características de Unity en Visual Studio para Mac

1. Visual Studio para Mac proporciona acceso rápido a documentación de Unity en el editor de código. Coloque el cursor en algún lugar en el **Vector3** de símbolos dentro de la **actualización** método y presione **⌘ comando + '** .

    ![Seleccionar método de visual studio para el editor de mac](media/unity-image38.png)

2. Se abre una nueva ventana del explorador en la documentación de **Vector3**. Cierre la ventana del explorador si se cumplen.

    ![ventana del explorador se abre en la documentación](media/unity-image39.png)

3. Visual Studio para Mac también proporciona algunas aplicaciones auxiliares para crear rápidamente clases de comportamiento de Unity. Desde **el Explorador de soluciones**, haga clic en **activos** y seleccione **Agregar > nuevo MonoBehaviour**.

    ![nueva acción de contexto de monobehaviour](media/unity-image40.png)

4. La clase recién creada proporciona código auxiliar para el **iniciar** y **actualización** métodos. Después de la llave de cierre de la **actualización** método, comience a escribir **"onmouseup"** . A medida que escribe, observe que IntelliSense de Visual Studio rápidamente los ceros el método que se va a implementar. Selecciónelo en la lista Autocompletar proporcionado. Van a rellenar un código auxiliar del método automáticamente, incluidos los parámetros.

    ![IntelliSense en visual studio para mac](media/unity-image41.png)

5. Dentro de la **OnMouseUp** método, tipo **"base".** Para ver todos los métodos bases disponibles para llamar a. También puede explorar las diferentes sobrecargas de cada función con la opción de paginación en la esquina superior derecha de la ventana flotante de IntelliSense.

    ![exploración de las sobrecargas en visual studio para mac](media/unity-image42.png)

6. Visual Studio para Mac también le permite definir fácilmente los sombreadores de nuevo. Desde **el Explorador de soluciones**, haga clic en **activos** y seleccione **Agregar > nuevo sombreador**.

    ![nueva acción de sombreador en visual studio para mac](media/unity-image43.png)

7. El formato de archivo de sombreador obtiene todo color y tratamiento de la fuente para que sea más fácil de leer y comprender.

    ![Resaltado de sintaxis](media/unity-image44.png)

8. Vuelva a **Unity**. Verá que, dado que Visual Studio para Mac funciona con el mismo sistema de proyecto, los cambios realizados en cualquier lugar se sincronizan automáticamente con las demás. Ahora es fácil de usar siempre la mejor herramienta para la tarea.

    ![panel activos de Unity](media/unity-image45.png)

## <a name="summary"></a>Resumen

En este laboratorio, ha aprendido cómo empezar a crear un juego con Unity y Visual Studio para Mac. Consulte [ https://unity3d.com/learn ](https://unity3d.com/learn) para obtener más información acerca de Unity.
