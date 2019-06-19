---
title: Introducción a la creación de juegos con Unity en Visual Studio para Mac
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
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Introducción a la creación de juegos con Unity en Visual Studio para Mac 

Unity es un motor de juego que permite desarrollar juegos en C#. En este tutorial se muestra cómo empezar a desarrollar y depurar juegos de Unity con Visual Studio para Mac y la extensión Visual Studio for Mac Tools for Unity junto con el entorno de Unity.

Visual Studio for Mac Tools for Unity es una extensión gratuita instalada con Visual Studio para Mac. Permite a los desarrolladores de Unity aprovechar las características de productividad de Visual Studio para Mac, lo que incluye la excelente compatibilidad de IntelliSense, las características de depuración, etc.

## <a name="objectives"></a>Objetivos

> [!div class="checklist"]
> * Obtenga información sobre el desarrollo de Unity con Visual Studio para Mac

## <a name="prerequisites"></a>Requisitos previos

- Visual Studio para Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition o superior ([https://store.unity.com](https://store.unity.com/), requiere una cuenta de unity.com para ejecutarse)

## <a name="intended-audience"></a>Destinatarios

Este laboratorio está destinado a desarrolladores familiarizados con C#, aunque no se requiere una experiencia profunda.

## <a name="task-1-creating-a-basic-unity-project"></a>Tarea 1: Creación de un proyecto básico de Unity

1. Inicie **Unity**. Si se le pide, inicie sesión.

2. Haga clic en **Nuevo**.

    ![Botón Nuevo de Unity](media/unity-image1.png)

3. Establezca el **Nombre del proyecto** en **"UnityLab"** y seleccione **3D**. Haga clic en **Crear proyecto**.

    ![Pantalla de creación de nuevo proyecto](media/unity-image2.png)

4. Ahora está viendo la interfaz predeterminada de Unity. Tiene la jerarquía de la escena con objetos del juego a la izquierda, una vista en 3D de la escena en blanco en la parte central, un panel de archivos de proyecto en la parte inferior y el inspector y los servicios a la derecha. Por supuesto, hay mucho más que eso, pero estos son algunos de los componentes más importantes.

    ![Interfaz de Unity en blanco](media/unity-image3.png)

5. Para los desarrolladores nuevos en Unity, todo lo que se ejecuta en la aplicación existe en el contexto de una **escena**. Un archivo de escena es un archivo único que contiene todo tipo de metadatos sobre los recursos usados en el proyecto para la escena actual y sus propiedades. Al empaquetar la aplicación para una plataforma, la aplicación resultante termina por ser una colección de una o más escenas, además de cualquier código dependiente de la plataforma que se agregue. Puede tener tantas escenas como quiera en un proyecto.

6. La nueva escena solo tiene una cámara y una luz direccional. Una escena requiere una **cámara** para que algo sea visible y un **cliente de escucha de audio** para que algo sea audible. Estos componentes están conectados a un elemento **GameObject**.

7. Seleccione el objeto **Cámara principal** en el panel **Jerarquía**.

    ![Objeto Cámara principal resaltado en el panel Jerarquía](media/unity-image4.png)

8. Seleccione el panel **Inspector** en el lado derecho de la ventana para revisar sus propiedades. Las propiedades de la cámara incluyen información de transformación, segundo plano, tipo de proyección, campo de visión, etc. También se ha agregado un componente de cliente de escucha de audio de forma predeterminada, que básicamente representa el audio de la escena desde un micrófono virtual conectado a la cámara.

    ![Panel Inspector](media/unity-image5.png)

9. Seleccione el objeto **Luz direccional**. Este proporciona luz a la escena para que componentes como los sombreadores sepan cómo representar objetos.

    ![Objeto Luz direccional resaltado](media/unity-image6.png)

10. Use el **Inspector** para ver que incluye propiedades comunes de iluminación como tipo, color, intensidad, tipo de sombra, etc.

    ![Examen de las propiedades del panel Inspector](media/unity-image7.png)

11. Es importante señalar que los proyectos de Unity son un poco diferentes a sus homólogos de Visual Studio para Mac. En la pestaña **Proyecto** de la parte inferior, haga clic con el botón derecho en la carpeta **Recursos** y seleccione **Mostrar en Finder**.

    ![Acción contextual Mostrar en Finder](media/unity-image8.png)

12. Los proyectos contienen las carpetas **Recursos**, **Biblioteca**, **ProjectSettings** y **Temp**, como se puede ver. Pero la única que se muestra en la interfaz es la carpeta **Recursos**. La carpeta **Biblioteca** es la caché local para los recursos importados; contiene todos los metadatos de los recursos. La carpeta **ProjectSettings** almacena las opciones que se pueden configurar. La carpeta **Temp** se usa para los archivos temporales de Mono y Unity durante el proceso de compilación. También hay un archivo de solución que se puede abrir en Visual Studio para Mac (**UnityLab.sln** aquí).

    ![Recursos en Finder](media/unity-image9.png)

13. Cierre la ventana **Finder** y vuelva a **Unity**.

14. La carpeta **Recursos** contiene todas las imágenes, el código, el audio, etc. de los recursos. Ahora está vacía, pero cada archivo que se incluya en el proyecto irá aquí. Esta es siempre la carpeta de nivel superior de **Unity Editor**. Agregue y quite archivos siempre a través de la interfaz de Unity (o Visual Studio para Mac) y nunca a través del sistema de archivos directamente.

    ![Carpeta Recursos de Unity](media/unity-image10.png)

15. **GameObject** es fundamental para el desarrollo en Unity, ya que prácticamente todo deriva de ese tipo, incluidos los modelos, las luces, los sistemas de partículas, etc. Agregue un nuevo objeto **Cubo** a la escena por medio del menú **GameObject > Objeto 3D > Cubo**.

    ![Objeto Cubo en escena](media/unity-image11.png)

16. Eche un vistazo rápido a las propiedades del nuevo tipo **GameObject** y vea que tiene un nombre, una etiqueta, una capa y una transformación. Estas propiedades son comunes para todos los tipos **GameObjects**. Además, se han asociado varios componentes al **Cubo** para proporcionar funcionalidad necesaria que incluye un filtro de malla, un colisionador de cuadros y un representador.

    ![Propiedades de GameObject](media/unity-image12.png)

17. Cambie el nombre del objeto **Cubo**, que tiene el nombre **"Cubo"** de forma predeterminada, a **"Enemigo"**. Asegúrese de presionar **Entrar** para guardar el cambio. Este va a ser el cubo enemigo de este juego sencillo.

    ![Propiedad de cambio de nombre del objeto Cubo](media/unity-image13.png)

18. Agregue otro objeto **Cubo** a la escena mediante el mismo proceso anterior y póngale el nombre **"Jugador"**.

    ![Cambio de nombre del segundo objeto Cubo](media/unity-image14.png)

19. Etiquete también el objeto de jugador **"Jugador"** (vea el control desplegable **Etiqueta** justo debajo del campo de nombre). Lo vamos a usar en el script de Enemigo para ayudar a localizar el objeto de juego Jugador.

    ![Etiquetado del objeto Jugador](media/unity-image15.png)

20. En la vista **Escena**, retire el objeto Jugador del objeto Enemigo a lo largo del eje Z con el mouse. Para moverse a lo largo del eje Z, seleccione y arrastre el cubo por su panel **rojo** hacia la línea **azul**. Puesto que el cubo se encuentra en el espacio 3D, pero solo se puede arrastrar en 2D cada vez, el eje en el que se arrastra es especialmente importante.

    ![Vista Escena que muestra un cubo](media/unity-image16.png)

21. Mueva el cubo hacia abajo y a la derecha a lo largo del eje. Esto actualiza la propiedad **Transform.Position** del **Inspector**. Asegúrese de arrastrar a una ubicación de forma similar a lo que se muestra aquí para facilitar los pasos posteriores del laboratorio.

    ![Movimiento de un cubo a lo largo del eje](media/unity-image17.png)

22. Ahora puede agregar algún código para controlar la lógica de Enemigo de modo que persiga a Jugador. Haga clic con el botón derecho en la carpeta **Recursos** del panel **Proyecto** y seleccione **Crear > Script de C#**.

    ![Acción contextual Script de C#](media/unity-image18.png)

23. Póngale el nombre **"EnemyAI"** al nuevo script de C#.

    ![Script de C#](media/unity-image19.png)

24. Para asociar scripts a objetos del juego, arrastre el script recién creado al objeto **Enemigo** en el panel **Jerarquía**. Ahora, ese objeto usa los comportamientos de este script.

    ![Resaltado que muestra la incorporación del script al objeto del juego](media/unity-image20.png)

25. Seleccione **Archivo > Guardar escenas** para guardar la escena actual. Asígnele el nombre **"MyScene"**.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Tarea 2: Trabajo con Visual Studio for Mac Tools for Unity

1. La mejor forma de editar código de C# es usar Visual Studio para Mac. Puede configurar Unity para usar Visual Studio para Mac como controlador predeterminado. Seleccione **Unity > Preferencias**.

2. Seleccione la pestaña **Herramientas externas**. En la lista desplegable **External Script Editor**, seleccione **Examinar** y luego **Applications/Visual Studio.app**. Si ya existe una opción **Visual Studio**, simplemente selecciónela.

    ![Pestaña Herramientas externas de Preferencias](media/unity-image21.png)

3. Unity está ahora configurado para usar **Visual Studio para Mac** para la edición de scripts. Cierre el cuadro de diálogo **Preferencias de Unity**.

    ![Visual Studio seleccionado en Preferencias](media/unity-image22.png)

4. Haga doble clic en **EnemyAI.cs** para abrirlo en **Visual Studio para Mac**.

    ![Recurso Enemigo seleccionado en Unity](media/unity-image23.png)

5. La solución de Visual Studio es sencilla. Contiene una carpeta **Recursos** (la misma de **Finder**) y el script **EnemyAI.cs** creado anteriormente. En proyectos más sofisticados, probablemente la jerarquía sea diferente a la que se ve en Unity.

    ![Panel Solución de Visual Studio para Mac](media/unity-image24.png)

6. **EnemyAI.cs** está abierto en el editor. El script inicial solo contiene códigos auxiliares para los métodos **Start** y **Update**.

7. Reemplace el código inicial de Enemigo por el código siguiente.

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

8. Eche un vistazo rápido al comportamiento sencillo de Enemigo definido aquí. En el método **Start**, se obtiene una referencia al objeto Jugador (por su etiqueta), así como su **transformación**. En el método **Update**, que se llama en cada fotograma, Enemigo se mueve hacia el objeto Jugador. Las palabras clave y los nombres usan codificación en colores para facilitar la comprensión del código base de Visual Studio para Mac.

9. Guarde los cambios en el script de Enemigo en **Visual Studio para Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Tarea 3: Depuración del proyecto de Unity

1. Establezca un punto de interrupción en la primera línea de código del método **Start**. Puede hacer clic en el margen del editor en la línea de destino o colocar el cursor en la línea y presionar **F9**.

    ![Establecimiento de punto de interrupción en Visual Studio para Mac](media/unity-image25.png)

2. Haga clic en el botón **Iniciar depuración** o presione **F5**. Con esto se compila el proyecto y se asocia a Unity para su depuración.

    ![Botón de inicio de Visual Studio para Mac](media/unity-image26.png)

3. Vuelva a **Unity** y haga clic en el botón **Ejecutar** para iniciar el juego.

    ![Botón Ejecutar de Unity](media/unity-image27.png)

4. Se debe alcanzar el punto de interrupción para poder usar las herramientas de depuración de Visual Studio para Mac.

    ![Punto de interrupción alcanzado en Visual Studio para Mac](media/unity-image28.png)

5. En el panel **Variables locales**, busque **este** puntero, que hace referencia a un objeto **EnemyAI**. Expanda la referencia y vea que puede examinar los miembros asociados, como **Velocidad**.

    ![Panel de depuración Variables locales de Visual Studio para Mac](media/unity-image29.png)

6. Quite el punto de interrupción del método **Start** del mismo modo que se agregó: ya sea haciendo clic en el margen o seleccionando la línea y presionando **F9**.

    ![Punto de interrupción alcanzado en Visual Studio para Mac](media/unity-image30.png)

7. Presione **F10** para ir a la primera línea de código donde se encuentre el objeto **Jugador** con una etiqueta como parámetro.

8. Mantenga el cursor del mouse sobre la variable **player** dentro de la ventana del editor de código para ver sus miembros asociados. Incluso puede expandir la superposición para ver las propiedades secundarias.

    ![Ventana de depuración del editor de Visual Studio para Mac](media/unity-image31.png)

9. Presione **F5** o el botón **Ejecutar** para continuar con la ejecución. Vuelva a Unity para ver el cubo Enemigo acercarse repetidamente al cubo Jugador. Es posible que necesite ajustar la cámara si no está visible.

    ![Escena reproducida en Unity](media/unity-image32.png)

10. Vuelva a **Visual Studio para Mac** y establezca un punto de interrupción en la primera línea del método **Update**. Se debe alcanzar inmediatamente.

    ![Establecimiento de un punto de interrupción en Visual Studio para Mac](media/unity-image33.png)

11. Imagine que la velocidad es demasiado rápida y quiere probar el impacto del cambio sin reiniciar la aplicación. Busque la variable **Velocidad** en la ventana **Automático** o **Variables locales**, cámbiela a **"10"** y presione **Entrar**.

    ![Ajuste de las variables en la ventana Variables locales](media/unity-image34.png)

12. Quite el punto de interrupción y presione **F5** para reanudar la ejecución.

13. Vuelva a **Unity** para ver la aplicación en ejecución. El cubo Enemigo ahora se mueve a una quinta parte de la velocidad original.

    ![Ventana de Unity con aplicación en ejecución](media/unity-image35.png)

14. Detenga la aplicación de Unity al volver a hacer clic en el botón **Reproducir**.

    ![Detención de la aplicación de Unity](media/unity-image36.png)

15. Vuelva a **Visual Studio para Mac**. Detenga la sesión de depuración al hacer clic en el botón **Detener**.

    ![Detención de la sesión de depuración en Visual Studio para Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Tarea 4: Examen de las características de Unity en Visual Studio para Mac

1. Visual Studio para Mac proporciona acceso rápido a documentación de Unity en el editor de código. Coloque el cursor en algún lugar del símbolo **Vector3** dentro del método **Update** y presione **⌘ Comando + '**.

    ![Selección de método en el editor de Visual Studio para Mac](media/unity-image38.png)

2. Se abre una nueva ventana del explorador para la documentación de **Vector3**. Cierre la ventana del explorador cuando esté satisfecho.

    ![Ventana del explorador con la documentación abierta](media/unity-image39.png)

3. Visual Studio para Mac también proporciona algunos asistentes para crear rápidamente clases de comportamiento de Unity. En el **Explorador de soluciones**, haga clic con el botón derecho en **Recursos** y seleccione **Agregar > Nuevo MonoBehaviour**.

    ![Acción contextual Nuevo MonoBehaviour](media/unity-image40.png)

4. La clase recién creada proporciona código auxiliar para los métodos **Start** y **Update**. Después de la llave de cierre del método **Update**, comience a escribir **"onmouseup"**. A medida que escribe, observe que IntelliSense de Visual Studio rápidamente sugiere el método que planea implementar. Selecciónelo en la lista Autocompletar proporcionada. Rellena un código auxiliar del método automáticamente, incluidos los parámetros.

    ![IntelliSense en Visual Studio para Mac](media/unity-image41.png)

5. Dentro del método **OnMouseUp**, escriba **"base."** para ver todos los métodos base disponibles a los que llamar. También puede examinar las diferentes sobrecargas de cada función con la opción de paginación de la esquina superior derecha del control flotante de IntelliSense.

    ![Examen de las sobrecargas de Visual Studio para Mac](media/unity-image42.png)

6. Visual Studio para Mac también permite definir fácilmente nuevos sombreadores. En el **Explorador de soluciones**, haga clic con el botón derecho en **Recursos** y seleccione **Agregar > Nuevo sombreador**.

    ![Acción Nuevo sombreador de Visual Studio para Mac](media/unity-image43.png)

7. El formato de archivo del sombreador obtiene tratamiento completo de color y fuente para facilitar su lectura y comprensión.

    ![Resaltado de sintaxis](media/unity-image44.png)

8. Vuelva a **Unity**. Puede ver que, dado que Visual Studio para Mac funciona con el mismo sistema de proyectos, los cambios realizados en cualquier lugar se sincronizan automáticamente con los demás. Ahora es fácil usar siempre la mejor herramienta para la tarea.

    ![Panel Recursos de Unity](media/unity-image45.png)

## <a name="summary"></a>Resumen

En este laboratorio ha aprendido cómo empezar a crear un juego con Unity y Visual Studio para Mac. Vea [https://unity3d.com/learn](https://unity3d.com/learn) para obtener más información sobre Unity.
