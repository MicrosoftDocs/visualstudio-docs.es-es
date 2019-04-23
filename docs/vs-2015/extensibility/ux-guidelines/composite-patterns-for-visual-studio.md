---
title: Patrones compuestos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3d719a52535614b8cddf1c31aeb97e41c7614767
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045088"
---
# <a name="composite-patterns-for-visual-studio"></a>Patrones compuestos para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Patrones compuestos combinan elementos de interacción y diseño de configuraciones distintas. Algunos de los patrones compuestos más importantes en Visual Studio con respecto a la coherencia incluyen:

- [Visualización de datos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfaz de usuario y leerlo de objeto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistencia y guardar la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="BKMK_DataVisualization"></a> Visualización de datos

### <a name="overview"></a>Información general
 Los gráficos son una forma visual para agregar y visualizar datos con el fin de mejorar la toma de decisiones. Pueden ayudar a los usuarios que se enfrentan con una gran cantidad de datos, pero poco lo que significa que vea lo que merece atención y lo que podría necesitar una acción.

 El usuario se beneficiará de un gráfico si se cumple alguna de las condiciones siguientes:

- ¿El gráfico ayudará a los usuarios identificar tareas que pueden actuar en?

- ¿El gráfico permite que los usuarios prever las consecuencias de posibles cambios?

- ¿El gráfico ayudará a los usuarios descubrir tendencias e identificar patrones?

- ¿El gráfico permite a los usuarios tomar decisiones mejor?

- ¿El gráfico ayudará a responder una pregunta específica que los usuarios pueden tener en el contexto especificado?

#### <a name="general-rules-for-charts"></a>Reglas generales para gráficos

- Claramente los datos de etiqueta. Ilustraciones sin explicación simplemente son prácticamente imágenes.

- Inicie los ejes en cero para evitar sesgar proporciones. Tamaño de longitud y la barra de la línea son importantes indicaciones visuales para entender las relaciones entre los puntos de datos.

- Crear gráficos, no infografías. Infografías son artísticas representaciones de datos y su objetivo principal es contar historias visual. Los gráficos pueden (y deben) resultar atractiva visualmente, pero deje que los datos hablen por sí mismos.

- Evite skeumorphism, gráficos de barras gráficos, almohadillas contraste y otros toques infografía.

- No utilice efectos 3D como elemento decorativo. Usarlas si solo se realmente parte integral de la capacidad del usuario para comprender la información.

- Evite el uso de varias líneas y rellenos, como más de dos colores pueden realizar este tipo de gráfico difícil de leer e interpretar correctamente.

- No use un gráfico (o cualquier ilustración) como el único medio de comprender un concepto o interactuar con los datos. Esto presenta dificultades para los usuarios con discapacidades visuales.

- No use gráficos como elementos decorativos o innecesarias en una página. En otras palabras, si no se agrega un gráfico de que cualquier valor o ayuda usuarios resolución un problema, no usarlo.

### <a name="chart-types"></a>Tipos de gráficos
 Tipos de gráficos que se usan en Visual Studio incluyen gráficos de barras, gráficos de líneas, un gráfico circular modificado que se conoce como un gráfico de anillos o "gráfico de anillos," escalas de tiempo, los trazados (también denominados "gráficos de clúster") y gráficos de Gantt de dispersión. Cada tipo de gráfico es útil para la comunicación de un tipo diferente de información.

### <a name="other-charting-considerations"></a>Otras consideraciones sobre la creación de gráficos

#### <a name="color"></a>Color
 Hay una paleta específica de los gráficos de colores definidos para su uso en Visual Studio. La paleta es accesible para los tipos principales de color rojo, y los colores se pueden diferenciar incluso cuando se usa como segmentos muy estrechos de color. Puede usar estos colores en cualquier combinación de cualquier tipo de gráfico o en la interfaz de usuario. No es necesario usar todos los colores de siete si no es necesario que muchos colores distintos. Estos colores no se diseñaron para usarse con los elementos de primer plano, por lo que no coloque texto o glifos encima de estos colores. Deben ser modificable y expuestos a la personalización del usuario en estos matices **Herramientas > opciones** (consulte [exponer los colores para los usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Muestrario|hex|RGB|
|------------|---------|---------|
|![Muestra 71B252](../../extensibility/ux-guidelines/media/0711-71b252.png "0711_71B252")|#71B252|113,178,82|
|![Muestra BF3F00](../../extensibility/ux-guidelines/media/0711-bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Swatch FCB714](../../extensibility/ux-guidelines/media/0711-fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Muestra 903F8B](../../extensibility/ux-guidelines/media/0711-903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Muestra 117AD1](../../extensibility/ux-guidelines/media/0711-117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Muestra 79D7F2](../../extensibility/ux-guidelines/media/0711-79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Muestra B5B5B5](../../extensibility/ux-guidelines/media/0711-b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="BKMK_OnObjectUI"></a> Interfaz de usuario y leerlo de objeto
 En esta sección se proporciona contexto a leerlo, también conocido como vista de inspección de código, un tipo de interfaz de usuario del objeto exclusivo de Visual Studio.

### <a name="overview"></a>Información general

- La interfaz de usuario en el objeto debe conceder al usuario obtener más información o interactividad sin apartarse de su tarea principal.

- El modelo principal para la interfaz de usuario del objeto en Visual Studio se conoce como "información en el punto de atención".

- Interfaz de usuario del objeto en Visual Studio es ya sea en línea o flotante y durable o transitorio.

  - Vista de inspección de código, un tipo de interfaz de usuario del objeto en Visual Studio, es duradero y en línea.

  - CodeLens, un tipo de interfaz de usuario del objeto en Visual Studio, es transitorio y flotantes

  Comprender cómo funciona un fragmento de código o buscar detalles sobre ese código, a menudo requiere un programador cambiar el contexto y vaya a otro tipo de contenido o en otra ventana. Estos cambios de contexto pueden ser problemático, ya que los usuarios pueden perder el foco en su tarea original si dejan su ventana principal. Además, la obtención de que copia original de contexto puede ser difícil, especialmente si cambio entre ventanas causa su código original para estar ocultado por otras interfaces de usuario.

  La interfaz de usuario en el objeto sigue un patrón llamado "información en el punto de atención". Estos mensajes, las ventanas emergentes y cuadros de diálogo proporcionar información adicional relevante que agrega alguna aclaración o interactividad sin perder el foco en su tarea principal a los usuarios. Algunos ejemplos de la interfaz de usuario del objeto son ventanas emergentes que aparecen cuando un usuario mantiene el puntero sobre un icono en el área de notificación, el subrayado ondulado de color rojo debajo de una palabra mal escrita y la vista de inspección introducido en Visual Studio 2013.

### <a name="decision-points"></a>Puntos de decisión
 Dentro de Visual Studio, hay varias formas de usar este patrón de información en el punto de atención. Elegir el mecanismo adecuado y su implementación de una manera coherente y predecible son esencial para la experiencia general. En caso contrario, podrían presentarse a los usuarios con una experiencia incoherente o confusa que resienta el foco desde el propio contenido.

#### <a name="relationships-between-master-and-detail-content"></a>Relaciones entre maestro y detalles de contenido
 Información en el momento de la atención se usa para mostrar una relación entre el contenido que el usuario está centrado en (el contenido "maestro") y adicionales relacionados con el contenido (el contenido de "Detalles"). En este patrón, el contenido de detalle está claramente relacionado con el contenido que el usuario está trabajando con y se puede mostrar el contenido principal cerca de. Información adicional o información que no se pueden resumir sin sobrecargar el contenido principal debe seguir otro patrón, como una ventana de herramientas.

- **Siempre** mostrar el contenido de detalle cerca al contenido principal.

- **Siempre** asegurarse de que el contenido de detalle aún permite que un usuario permanece centrado en el contenido principal. A menudo, la mejor manera de lograr esto es representar el contenido de detalle como cerca el contenido principal como sea posible. Esto puede hacerse al representar el contenido de detalle en una ventana emergente junto al contenido principal o al representar el detalle contenido en línea debajo el contenido principal.

- **Nunca** usar información en el momento de la atención que lleva al usuario fuera el contenido principal. Si los usuarios necesitan ver el contenido de detalle por separado, exponer una acción explícita que permite al usuario hacer esto.

#### <a name="design-details"></a>Detalles de diseño
 Cuando haya determinado que la interfaz de usuario en el objeto es la elección correcta, hay cuatro consideraciones de diseño principal:

1. **Persistencia:** se espera el contenido sea duradero o transitorio?
   ¿Los usuarios querrán que sean visibles para hacer referencia a o para interactuar con la información? ¿O bien, los usuarios desearán rápidamente Eche un vistazo a la información y, a continuación, continuar con su tarea principal?

2. **¿Tipo de contenido:** el contenido será informativo, útiles o navegación?
   ¿El usuario necesita información adicional sobre el contenido principal? ¿El usuario necesita completar una tarea que afecta al contenido principal? ¿O el usuario deberá dirigirse a otro recurso?

3. **¿Tipo de indicador:** tiene un indicador de ambiente sentido?
   ¿Puede la información de resumen de una manera útil y mostrar sin sobrecargar el contenido principal?

4. **Movimientos:** gestos de lo que se usará para invocar y descartar la interfaz de usuario?
   ¿Cómo mostrar el contenido de detalle y enviarlo fuera el usuario? ¿Existe valor agregando un gesto, como anclado para cambiar entre estados transitorios y durable?

   Cada uno de estos puntos de cuatro decisión tendrá un impacto en los principales componentes de interfaz de usuario del objeto.

### <a name="on-object-ui-components"></a>Componentes de interfaz de usuario del objeto

1. Tipo de contenedor (ranura de contenido)

    - Flotante

    - Alineado

2. Tipo de contenido

    - Informativo: datos que podrían ser estática o dinámica

    - Que requieren acción: los comandos que cambian el contenido principal

    - Navegación: vínculos que llevan al usuario a otra ventana o aplicación, como MSDN

3. Gestos

    - Invocación

    - Despido

    - Anclar

    - Otras interacciones

4. Modelo de persistencia y confirmación

    - Transitorio

    - Durable

    - Automático

    - Y a petición

5. Indicadores de ambientales (opcionales)

    - Subrayado de subrayado ondulado de color

    - Icono de etiqueta inteligente

    - Otros indicadores de ambientales

#### <a name="container-content-presenter-type"></a>Tipo de contenedor (ranura de contenido)
 Hay dos opciones principales presentar contenido en el punto de atención:

1. **Insertado:** espacio para el nuevo contenido hace que un moderador en línea, como la vista de inspección que se introdujo en el Editor de código de Visual Studio 2013, trasladando el contenido existente.

    - **Prefiere** insertada presentadores si espera que los usuarios desearán dedicar una cantidad considerable de tiempo que hace referencia a o interactuar con el contenido presente.

    - **Evitar** insertada presentadores si espera que los usuarios desearán Eche un vistazo a la información que presenta y luego continuar con su tarea principal con una interrupción mínima.

2. **Flotante:** un presentador flotante se coloca lo más cerca del contenido seleccionado como sea posible, pero no modifica el diseño del contenido existente. Se pueden emplear diversas estrategias, como mostrar un panel flotante contenido a través de la más cercana disponible espacio en blanco en el símbolo seleccionado.

    - **Prefiere** flotante presentadores si espera que los usuarios desearán Eche un vistazo a la información que presenta y luego continuar con su tarea principal con una interrupción mínima.

    - **Evitar** flotante presentadores si espera que los usuarios querrán que dedicar una cantidad considerable de tiempo que hace referencia a o interactuar con el contenido se presente.

#### <a name="content-type"></a>Tipo de contenido
 Hay tres tipos principales de contenido que se pueden mostrar dentro de cualquier contenedor de interfaz de usuario del objeto. Se puede mostrar cualquier combinación de estos tipos de información. Los tres tipos son:

1. **Informativo:** contenedores de la interfaz de usuario mostrará algún tipo de contenido informativo del objeto de la mayoría. El contenido puede representar la información sobre el estado actual del entorno o puede representar información sobre un estado futura potencial del entorno. Por ejemplo, podría usarse para mostrar el efecto de un comando concreto, como una refactorización en el código existente.

    - **Siempre** usar la representación canónica de la información que mostrar. Por ejemplo, el código debería ser similar a código, junto con el resaltado de sintaxis y debe respetar la fuente y otras opciones de entorno que el usuario ha establecido.

    - **Siempre** considere la posibilidad de admitir las acciones sobre el contenido informativo que sería posible si esa misma información se presenta como contenido principal. Por ejemplo, si el código existente dentro de un contenedor de interfaz de usuario del objeto a presentar, fuertemente considere la posibilidad de admitir la capacidad de examinar y modificar ese código.

    - **Siempre** considere el uso de un color de fondo diferente si presentar el contenido informativo que representa un estado futuro potencial.

2. Procesables: algunos contenedores de la interfaz de usuario del objeto proporcionará la capacidad de realizar alguna acción sobre el contenido principal, como realizar una operación de refactorización.

    - **Siempre** colocar comandos procesables por separado desde el contenido informativo.

    - **Siempre** habilitar y deshabilitar las acciones cuando corresponda.

    - **Siempre** hacen referencia a las directrices estándar para representar comandos dentro de los cuadros de diálogo.

    - **Siempre** mantener el número de acciones que se exponen en absoluto de un contenedor de objeto la interfaz de usuario mínima. Interactuar con la interfaz de usuario del objeto debe ser una experiencia ligera y rápida. El usuario no debe tener que gastar energía acerca de cómo administrar el contenedor del objeto de interfaz de usuario.

    - **Siempre** considerar cómo y cuándo se cierra o descartar un contenedor de la interfaz de usuario del objeto. Como práctica recomendada, cualquier acción que concluye el cuadro de diálogo entre el maestro y detalles de contenido también debe cerrar el contenedor de la interfaz de usuario del objeto cuando se invoca esa acción.

3. **Navegación:** algunos en objetos contenedores de la interfaz de usuario incluyen vínculos que llevan al usuario a otra ventana o aplicación, como la apertura de un artículo MSDN en el explorador web del usuario.

    - **Siempre** anteponer cualquier vínculo de navegación con "Abrir" para que los usuarios no sorprenderá por algún otro contenido que se navega.

    - **Siempre** separar los vínculos de navegación de vínculos útiles.

#### <a name="ambient-indicators-optional"></a>Indicadores de ambientales (opcionales)
 Indicadores de ambientales pueden ser sutil, incluido el texto presentado en un color de contraste del resto del código, u obvio, incluidos los símbolos tickler como subrayados subrayado ondulado de color e iconos de etiqueta inteligente. Indicadores de ambientales comunican la disponibilidad de información adicional relevante. Lo ideal es que, incluso sin solicitar al usuario interactuar con ellos proporcionan información útil.

- **Siempre** colocar un indicador de ambiente para que no distraer o sobrecargando el usuario. Si no es posible colocar un indicador de ambiente de tal manera, considere la posibilidad de otra solución.

- **Siempre** colocar lo antes posible para el contenido que está relacionado con el indicador de ambiente.

- **Siempre** intenta crear un indicador que resume la información hace que estén disponible. Considere proporcionar un recuento del número de elementos de datos disponibles (por ejemplo, "3 referencias" en lugar de simplemente "Referencias") o pensar en alguna otra forma de resumir los datos.

    - En casos donde los datos de un indicador no siempre se calcula y muestra, considere inmediatamente comentarios progresiva tal como se calculan los valores. Por ejemplo, considere la posibilidad de animar los cambios que reflejan las actualizaciones de los datos disponibles, similares a la manera en que se actualiza el icono dinámico de correo electrónico en Windows Phone como el número de correos electrónicos no leídos aumenta.

- **Nunca** agregar indicadores más que un usuario puede tardar bastante para una parte determinada del contenido. Indicadores de ambientales deben ser útiles sin necesidad de ninguna interacción del usuario. Indicadores de perderán su ambiente si requieren desbordamiento y otros controles de administración para ponerlos en la vista.

#### <a name="gestures"></a>Gestos
 Un aspecto clave de permitir que el usuario mantener el foco en el contenido principal está proporcionando los gestos derechos para abrir y descartar el contenido de detalles adicionales.

- **Siempre** requieren que el usuario realizar algunas gesto explícito para abrir el contenido adicional. Gestos abiertos comunes incluyen:

    - **Al mantener el mouse:** información sobre herramientas o contenido informativo no interactivo

    - **Comando explícito:** moderador en línea

    - **Haga doble clic en el indicador de ambiente:** Ventana emergente de CodeLens

- **Siempre** descartar el contenido de detalle siempre que el usuario presiona la tecla Esc.

- **Siempre** tenga en cuenta el contexto de la interfaz de usuario del objeto. Moderadores de contenido que permiten la interacción dentro del contenedor, prestar si se debe mostrar información adicional al mantener el mouse, que suele ser perjudiciales para el flujo de trabajo del usuario.

- **Nunca** mostrar contenido al mantener el mouse que parece ser editable o invitaciones a la interacción del usuario. Este comportamiento puede frustrar a los usuarios si intenta mover el cursor sobre el contenido de detalle, como es el comportamiento estándar para una información sobre herramientas descartar inmediatamente cuando el cursor ya no está sobre el patrón de contenido que lo generó.

## <a name="BKMK_SelectionModels"></a> Modelos de selección

### <a name="overview"></a>Información general
 Un modelo de selección es el mecanismo utilizado para indicar y confirmar las operaciones en uno o más objetos de interés dentro de la interfaz de usuario. Este tema describen los patrones de interacción de selección en los editores de documento de Visual Studio: las superficies de modelado, superficies de diseño y editores de texto.

 Los usuarios deben tener una forma de indicar a Visual Studio, lo que están trabajando, y Visual Studio debe responder de forma predecible con comentarios a los usuarios sobre lo que se está ejecutando en. Puede dar lugar a una falta de comunicación entre el usuario y la interfaz de usuario o de diferencias en el usuario no advertir una acción, que puede tener consecuencias no deseadas. A menudo, el error pasa desapercibido hasta que el usuario ve que falta algo o ha cambiado. Los modelos de selección son, por tanto, una de las partes más importantes del diseño de la interfaz de usuario. Aunque los modelos de selección en Visual Studio son coherentes con Windows, hay pequeñas variaciones.

 En Visual Studio, como en Windows, los modelos de selección varían según el contexto en el que se produce la interacción. Selecciones pueden producirse en cuatro tipos de objetos:

- Texto

- Objetos gráficos

- Listas y árboles

- Cuadrículas

  Dentro de estos objetos, hay tres tipos de selecciones:

- Contiguos

- No contiguo

- Región

#### <a name="scope"></a>Ámbito
 El componente más importante de selección es asegurarse de que el usuario sabe en qué ventana funcionan (activación) y dónde el foco se encuentra (selección). Visual Studio extiende la funcionalidad de administración de la ventana de Windows, pero el esquema de activación es el mismo: interactuar con una ventana trae el foco a la ventana. Visual Studio tiene dos indicadores para la activación: uno para las ventanas de documento y otro para las ventanas de herramientas.

 Para las ventanas de documento, la ventana activa se indica mediante una ficha de ventana de documento llega a la parte delantera y cambiar su color de fondo:

 ![Selección de pestaña activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-01-activetab.png "0713 01_ActiveTab")

 **Selección de pestaña activa**

 Ventanas de herramientas, la ventana activa se indica mediante un cambio en el color del área de la barra de título de la ventana de herramientas:

 ![Selección de la ventana de herramientas activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-02-activetoolwindow.png "0713 02_ActiveToolWindow")

 **Ventana de herramientas activa, se muestra la selección principal de un nodo**

 ![Selección de la ventana de herramientas inactiva en Visual Studio](../../extensibility/ux-guidelines/media/0713-03-inactivetoolwindow.png "0713 03_InactiveToolWindow")

 **Ventana de herramientas inactiva, se muestra la selección latente del nodo**

 Una vez que una ventana está activa, se indica la importancia según los modelos de selección que se describen en esta sección de las instrucciones.

#### <a name="context"></a>Contexto
 Visual Studio fue diseñado para conservar un fuerte concepto de contexto, realizando un seguimiento de donde el usuario está trabajando. Sólo una ventana está activa, ya sea una ventana de herramientas o documento. Sin embargo, la ventana de documento superior siempre conserva una selección latente. Aunque el foco esté en una ventana de herramientas, la ventana de documento que estuvo activo muestra una selección, incluso en un estado inactivo. Esto sirve para conservar el contexto del usuario en el documento que estaba editando, que se muestra que Visual Studio conserva su estado para que puede devolver- and -shift sin problemas entre las ventanas de herramientas y ventanas de documento.

### <a name="text-selection"></a>Selección de texto
 Los editores de Visual Studio que son estrictamente textuales, como el editor de texto integrado, usan el mismo modelo de selección de texto y aspecto se describe en el [Mouse y punteros](https://msdn.microsoft.com/library/dn742466.aspx) página de Windows User Experience Interaction Guidelines en MSDN. El foco de entrada en el editor de texto se indica mediante una barra vertical que llama el punto de inserción. El punto de inserción es un solo píxel grueso y color como el inverso de todo lo que aparece detrás de él. Parpadeará según la frecuencia establecida el **velocidad de intermitencia del Cursor** en el **velocidad** pestaña de la **teclado** applet del Panel de Control.

#### <a name="contiguous-and-disjoint-selection"></a>Selección contigua y separada
 Solo es contiguo selección dentro del editor de texto. No se permiten selecciones, pero se deben solucionar en el Editor de gráficos de objeto de texto inconexos. Cuando el puntero del mouse está sobre un área de texto, el cursor cambia a un cursor en i. Un solo clic coloca el punto de inserción en el editor de texto en la posición del clic. Manteniendo presionado el botón del mouse se inicia un área resaltada de selección y soltar el botón del mouse finaliza el resalte de la selección.

#### <a name="region-selection-box-selection"></a>Selección de región (selección del cuadro)
 Visual Studio admite selecciones de la región en el editor de texto, y esto se conoce como selección del cuadro. Selección del cuadro permite al usuario seleccionar un área de texto que no sigue la secuencia de texto normal. Al igual que con la selección de texto estándar, la selección debe ser contigua. Selección del cuadro inicia manteniendo presionada la tecla Alt mientras arrastra el mouse. También se puede iniciar la selección del cuadro manteniendo presionadas las teclas de MAYÚS y Alt mientras usa las teclas de flecha para indicar la región de selección. Selección del cuadro usa el resaltado de selección normal y muestra el cursor parpadea al final del área de selección del punto de inserción.

 ![Regional &#40;cuadro&#41; selección en Visual Studio](../../extensibility/ux-guidelines/media/0713-04-boxselection.png "0713 04_BoxSelection")

 **Selección de región (cuadro) en Visual Studio**

#### <a name="text-selection-appearance"></a>Apariencia de la selección de texto
 Se pueden personalizar los colores utilizados para la selección activa e inactiva en el editor. Para personalizar la apariencia visual del editor, un usuario puede ir a **Herramientas > opciones**y, a continuación, busque en **entorno > fuentes y colores > Editor de texto**.

### <a name="graphical-selection"></a>Selección gráfico

#### <a name="interaction"></a>Interacción
 Selección de objetos gráficos puede ser compleja y depende de una serie de factores:

- **Modelo de selección principal del editor.** Los editores que contienen objetos gráficos también pueden utilizarse para editar texto o cuadrículas. Por ejemplo, el editor podría ser un editor de texto que también admite la colocación de objetos gráficos, como el Diseñador XAML de Visual Studio. Compatibilidad con varios tipos de objeto puede afectar a cómo el usuario selecciona grupos consta de diferentes tipos de objetos.

- **Compatibilidad con los Estados de selección principal y secundaria.** Un editor puede proporcionar la selección primaria y secundaria, los Estados para que se pueden editar los objetos al unísono, están alineados entre sí, cambiar de tamaño juntos, y así sucesivamente.

- **Compatibilidad con la edición en contexto.** Los editores también pueden permitir que el contenido de sus objetos gráficos que se va a editar. Por ejemplo, una forma de rectángulo también podría contener texto en el interior que puede cambiarse por el usuario. Además, que el texto se podría centrado o justificado. Edición en contexto implica un nivel más detallado de la interacción del usuario y, por tanto, requiere un conjunto apropiado de indicaciones visuales para presentar información de estado al usuario.

#### <a name="mouse-interaction"></a>Interacción con el mouse

|Entrada|Resultado|
|-----------|------------|
|Haga clic en un objeto no seleccionado|Selecciona el objeto y muestra una línea discontinua y controladores de selección, si el objeto es de tamaño ajustable.|
|Haga clic en un objeto seleccionado|Activa la edición en contexto, si lo admite el objeto. Se hace clic fuera del objeto, desactiva el modo de edición en contexto.|
|Haga doble clic en un objeto|Se abre el código detrás del objeto para su edición y podría insertar un controlador de eventos de forma predeterminada, si procede.|
|Seleccione un objeto|Cambia el puntero hasta el cursor de movimiento. Puede cambiar la apariencia del objeto, como su luminosidad o un color.|
|Elija un controlador de selección|Cambia el puntero hasta el cursor de cambio de tamaño. Para los objetos que admiten el giro, algunos controladores de selección pueden cambiar el puntero a un cursor Girar tal como se sitúa el puntero diferente (por ejemplo, si se mueve más lejos) en relación con el controlador de selección.|
|Arrastre|Incluso si el objeto no se ha seleccionado anteriormente, cambia el puntero hasta el cursor de movimiento y mueve el objeto.|
|Editor pierde el foco|Desactiva el modo de edición en contexto, aunque el objeto conserva el contenido y el aspecto que tenía durante su último estado de operación o selección.|
|Selección de objetos|Indicado por un borde, línea de puntos u otro tratamiento distingan visualmente para resaltar el límite del objeto.|
|Cambiar el tamaño de un objeto seleccionado|Indicado por controladores de selección.<br /><br /> Un objeto redimensionable tiene ocho controladores, que representa cada dirección en la que puede cambiarse. Si el objeto sólo se puede cambiar el tamaño en determinadas direcciones, se pueden usar menos identificadores. Cuando el usuario cambia el tamaño de un objeto hasta donde ocho controladores no ser interactivas, se pueden usar cuatro identificadores. Tamaños de identificador deben asociarse a las métricas de borde y el borde de ventana con el **GetSystemMetrics** función al tamaño proporcional a la resolución de pantalla de la API.<br /><br /> ![Controladores de tamaño](../../extensibility/ux-guidelines/media/0713-05-resizehandles.png "0713 05_ResizeHandles")|
|Girar un objeto seleccionado|![Controladores de giro](../../extensibility/ux-guidelines/media/0713-06-rotate.png "0713 06_Rotate")|

#### <a name="keyboard-interaction"></a>Interacción con el teclado

|Entrada|Resultado|
|-----------|------------|
|Tab|Mueve el indicador de foco entre el orden lógico de objetos en el editor. Esto puede ser de izquierda a derecha o arriba a abajo según **TabIndex** (o equivalentes) el valor de propiedad, orden de creación de objetos y el propósito general del editor. Mayús + Tab invierte la dirección del indicador de foco.|
|Barra espaciadora|Activa el modo de panorámica mientras se mantiene la pulsación de tecla. Entrada de mouse adicional es necesario para realizar una panorámica de la posición de la ventanilla.|
|Ctrl+Barra espaciadora|Activa el modo de zoom mientras se mantiene la pulsación de tecla. Se requiere entrada de mouse adicionales para aumentar y disminuir el factor de zoom.|
|Ctrl + Alt + signo menos|Disminuye el factor de zoom en un nivel.|
|Ctrl + Alt + signo más|Aumenta el factor de zoom en un nivel.|
|Tecla MAYÚS o Ctrl|Agrega el objeto al grupo de selección. CTRL también permite quitar los objetos por separado desde el grupo de selección.|
|Entrar|Realiza el comando predeterminado del objeto (normalmente se abre o editar).|
|F2|Activa la edición en contexto para el objeto.|
|Teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla presionada, en incrementos pequeños (por ejemplo, de 1 píxel en un momento)|
|CTRL + las teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla presionada, en incrementos mayores (por ejemplo, 10 píxeles a la vez)|
|Mayús + flecha claves|Cambia el tamaño de los objetos seleccionados en la dirección correspondiente, en incrementos pequeños (por ejemplo, de 1 píxel en un momento)|
|Ctrl + Mayús + teclas de dirección|Cambia el tamaño de los objetos seleccionados en la dirección correspondiente, en incrementos mayores (por ejemplo, 10 píxeles a la vez)|

 Cuando los usuarios modificar controles en su lugar, tendría sentido para los objetos cambiar el tamaño automáticamente con la entrada del usuario. Por ejemplo, si el usuario edita un control de etiqueta, la etiqueta debe crecer para mostrar el texto que escribió el usuario. Si no se hace esto, el usuario debe cambiar el tamaño del control manualmente después de editar el texto. Si el usuario tiene una gran cantidad de controles, esto se convierte en una tarea improductivo y básicas.

#### <a name="graphical-containers"></a>Contenedores de gráficos
 En algunos casos, editores gráficos proporcionan contenedores para otros objetos gráficos, como el control de Panel de formularios Windows Forms o el control de diseño de cuadrícula en el Diseñador HTML. Si el editor proporciona contenedores para otros objetos gráficos, debe utilizarse el siguiente modelo de selección para el contenedor solo (objetos en el seguimiento de contenedor del modelo estándar como se ha descrito anteriormente):

|Entrada|Resultado|
|-----------|------------|
|Hacer clic en el contenedor|Selecciona el objeto contenedor sin directamente la selección de cualquiera de los objetos contenidos. El contenedor se puede mover o cambiar de tamaño con estándar mouse y teclado (como se describió anteriormente). Los objetos contenidos se mueven en relación al contenedor, pero no cambian de tamaño los objetos contenidos a menos que se seleccionan directamente.|
|Mantenga el mouse sobre la región de límites del contenedor|El mouse se convierte en el cursor de movimiento, que indica que se puede mover el contenedor.|
|Arrastre la región de límites del contenedor|Cambia el mouse hasta el cursor de movimiento y mueve el contenedor (y los objetos contenidos dentro de). El contenedor no se pueden mover sin primero seleccionado con un solo clic.|
|Hacer clic en un objeto dentro del contenedor|Anula el contenedor (si ha seleccionado) y selecciona sólo el objeto hace clic en él.|
|Mayús + clic o Ctrl + clic en un contenedor o un objeto contenido|Agrega el objeto donde ha hecho clic en un grupo de selección o la selección existente. Si el objeto que se hace clic en él ya es miembro del grupo de selección, se quita el grupo de selección.|

 El modelo de selección básica deben cumplir los objetos contenidos como se describe en la sección anterior. Pruebas de facilidad de uso del Diseñador de Windows Forms, espera que los usuarios un acceso ininterrumpido a los objetos contenidos sin intervención de pasos (impuestas por el objeto de contención).

#### <a name="disjoint-and-region-selections"></a>No contiguo y las selecciones de región
 Editores de objeto gráfico deben admitir selecciones discontinuas. Tenga en cuenta que este gráfico no muestra la apariencia del control para Visual Studio. Consulte [apariencia de la selección de objeto gráfico](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) para obtener especificaciones detalladas visuales.

 ![No contiguo y selectores de región](../../extensibility/ux-guidelines/media/0713-07-disjointregionselectors.png "0713 07_DisjointRegionSelectors")

 **Selección no contiguo**

 Editores gráficos también deben proporcionar las selecciones de la región con un indicador de selección de tipo marquesina. Si el editor gráfico admite otros tipos de objeto (por ejemplo, texto), a continuación, las selecciones de la región es posible que no sea posibles según las restricciones de esos otros tipos de objeto.

 ![Selección de recuadro](../../extensibility/ux-guidelines/media/0713-08-marqueeselection.png "0713 08_MarqueeSelection")

 **Selección de recuadro**

#### <a name="primary-and-secondary-selections"></a>Selecciones principal y secundaria
 Algunos editores de objeto gráfico permiten al usuario editar o alinear objetos en grupos. En este caso, debe introducir el concepto de selecciones principal y secundaria. La selección principal es el objeto al que todos los demás objetos responden para las operaciones de grupo. El objeto que el usuario selecciona el primero se convierte en el control principal y las selecciones subsiguientes se convierten en las selecciones secundaria. La selección primaria tiene un tratamiento distinto visual de las selecciones para indicar que el objeto que es el principal secundarios:

 ![Selección primaria y secundaria](../../extensibility/ux-guidelines/media/0713-09-primarysecondary.png "0713 09_PrimarySecondary")

 **Selección primaria con dos selecciones secundarias**

#### <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apariencia de la selección de objeto gráfico
 Los controladores de selección son cuadrados dibujadas en un patrón rectangular alrededor del rectángulo del objeto. El gráfico siguiente muestra ejemplos de los diferentes Estados que puede tener un objeto gráfico con el identificador, ajuste de tamaño y apariencia de edición en contexto. El tamaño de los identificadores debe asociarse al borde de ventana y el uso de las métricas de edge el **GetSystemMetrics** API.

|          Estado          |  Apariencia   |                                                                  Detalles de Visual                                                                  |
|-------------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
|     **No seleccionado**      |    Default    |                 ![Estado del botón predeterminado](../../extensibility/ux-guidelines/media/0713-10-defaultstate.png "0713 10_DefaultState")                 |
|  **Selección primaria**  |   Puede cambiar el tamaño   |       ![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-11-primaryresize.png "0713 11_PrimaryResize")        |
|  **Selección primaria**  | No puede cambiar el tamaño |    ![Selección primaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-13-primarynoresize.png "0713 13_PrimaryNoResize")    |
|  **Selección primaria**  |    Bloqueado     |              ![Selección primaria bloqueada](../../extensibility/ux-guidelines/media/0713-15-primarylocked.png "0713 15_PrimaryLocked")              |
| **Selección secundaria** |   Puede cambiar el tamaño   |    ![Selección secundaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-17-secondaryresize.png "0713 17_SecondaryResize")     |
| **Selección secundaria** | No puede cambiar el tamaño | ![Selección secundaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-19-secondarynoresize.png "0713 19_SecondaryNoResize") |
| **Selección secundaria** |    Bloqueado     |           ![Selección secundaria bloqueada](../../extensibility/ux-guidelines/media/0713-21-secondarylocked.png "0713 21_SecondaryLocked")           |
|      **Interfaz de usuario activo**      |    Default    |                       ![Estado de IU active](../../extensibility/ux-guidelines/media/0713-23-uiactive.png "0713 23_UIActive")                        |

### <a name="view-selection-models"></a>Modelos de selección de vista

#### <a name="tree-view"></a>Vista de árbol
 Se muestra la selección en una vista de árbol con un simple resaltado. Si el usuario hace clic en un nombre de nodo o un icono de nodo, se selecciona el nodo. Los glifos triangulares a la izquierda del nodo expanda o el control de árbol de contrato, pero no afectan a la selección del usuario, con una excepción: tras contraer un nodo primario cuando la selección está en un elemento secundario de ese nodo, la selección se desplaza al elemento primario.

 ![Vista de árbol típica en Visual Studio](../../extensibility/ux-guidelines/media/0713-25-treeview.png "0713 25_TreeView")

 **Vista de árbol típica en Visual Studio**

 Vistas de árbol pueden admitir selecciones contiguas y no contiguas, incluso a través de varios niveles del árbol. Contiguos o no contiguos se deben realizar varias selecciones en los nodos de árbol visible. Si un nodo está contraído, se pierde la selección separada y el nodo que se contrajo Obtiene la selección. De este modo, el usuario puede ver los nodos que se verán afectados por una operación. Cuando se contraen los nodos, sea poco claro qué nodos pueden verse afectados.

 Cuando se selecciona un nodo primario, debe aplicar la operación con el elemento primario, aunque puede haber casos donde tenga sentido para una operación aplicar el elemento primario y todos sus elementos secundarios. En este caso, proporcionan la interfaz de usuario adicional durante la operación, como una casilla o un cuadro de diálogo de confirmación para que la opción "aplicar a todos los elementos secundarios" explícita para el usuario.

##### <a name="renaming"></a>Cambiar nombre
 Si los nodos del árbol admiten el cambio de nombre, cambiar el nombre debe realizarse en su lugar. La operación local debe ser el estándar en todos los controles de árbol en Visual Studio. Proporciona un comando de cambio de nombre que se activa inmediatamente el modo de edición en contexto, con la selección de texto que abarca el nombre completo del nodo, preparado para aceptar la entrada del usuario. Si el nodo representa un archivo, el nombre de archivo debe contener la extensión. Resaltado de la selección debe incluir sólo el cuerpo del nombre de archivo y no la extensión.

|Entrada|Resultado|
|-----------|------------|
|Entrar (tecla)|Confirma la operación de cambio de nombre|
|Tecla ESC|Cancela la operación de cambio de nombre|
|Hacer clic fuera de la región de edición en contexto|Confirma la operación de cambio de nombre|
|Undo|Proporcionar la fácil deshacer para cancelar la operación de cambio de nombre|

#### <a name="selection-within-lists-and-grid-controls"></a>Selección de listas y los controles de cuadrícula
 El concepto clave en la selección de la lista es que está basado en la fila, lo que significa que cuando se realiza una selección toda la fila está seleccionada como una unidad. Por el contrario, las cuadrículas pueden permitir que determinadas celdas que se seleccionen sin que afecte a todos los demás aspectos de la fila. Las cuadrículas también podrían contener una jerarquía de filas anidadas (como en un control TreeGrid) que permiten todas ramas de la jerarquía se seleccionen y se anula la selección mediante la interacción con las filas primarias. Selección de listas se muestra mediante un color de resalte simple en toda la fila de datos. El foco se muestra un borde de puntos solo píxel alrededor de la fila actual de editable o celda (fila si todas las celdas son de solo lectura).

> [!NOTE]
>  **Enfoque** y **selección** son conceptos diferentes. *Enfoque* es una indicación de que la interfaz de usuario del elemento que se destina para recibir entrada dirigido no explícitamente a otro objeto, mientras que *selección* se refiere al estado de inclusión de un objeto en un conjunto de objetos de los cuales posteriores las operaciones pueden tener lugar.

 Las selecciones en las listas pueden ser contiguas, separado, o la región. Cuando selecciones múltiples se permiten, contiguos y siempre debe ser compatible selección separado al soporte técnico para las selecciones de región (cuadro) son opcional. Las selecciones de región se inician y arrastrándola en el espacio en blanco del cuerpo de la lista.

| Object | Selección  |
|--------|------------|
|  Lista  | Contiguos |
|  Lista  |  No contiguo  |
|  Lista  |   Región   |

 Al hacer clic una vez en una lista, selecciona la fila donde se hizo clic. Si el usuario haga clic en una celda de la lista que admite la edición en contexto, la celda se activa inmediatamente para su edición en contexto. En caso contrario, toda la fila se selecciona inmediatamente y muestra un área resaltada.

 Arrastrar en el cuerpo de la lista, realiza una de estas tres cosas:

- Inicia una selección de región si lo admite la lista y el mouse hacia abajo que se encuentra en un espacio en blanco

- Inicia una operación de arrastrar y colocar, si la fila o celda de la lista admite que se va a un origen de arrastre

- Selecciona la fila actual

##### <a name="in-place-editing"></a>Edición en contexto
 Cuando se permite la edición en contexto, hay dos modelos básicos: selector de control y la propiedad de edición sencilla. Con un control de edición sencilla, el contenido está resaltado y listo para la entrada, en cuanto se activa la edición en contexto del usuario. Cuando se implementa un selector de propiedad, se muestra el botón que invoca el selector de propiedad una vez que se activará el modo de edición en contexto y la selección actual no está resaltada. El botón selector debe estar justificada a la derecha en la celda. Para obtener ejemplos de edición en contexto, vea el **ventana propiedades** y **lista de tareas** en Visual Studio.

##### <a name="keyboard-support"></a>Compatibilidad con el teclado
 Compatibilidad con el teclado para la selección en las listas y cuadrículas sigue las convenciones estándar de Windows:

- Teclas de dirección vaya a la lista de selección de cada celda de fila se mueve el foco.

- Mayús + flecha realiza una selección contigua en la dirección de las teclas de dirección.

- Ctrl + flecha seguido por la barra espaciadora alterna entre agregar y quitar elementos de la lista de la selección, creación de una selección no contiguo.

- Para las cuadrículas que contienen las jerarquías anidadas, la tecla flecha derecha expande una fila primaria y la tecla flecha izquierda contrae uno.

- La tecla Tab mueve el foco entre las celdas de la fila actual si las celdas se pueden modificables.

- La tecla ENTRAR, realiza el comando predeterminado en el elemento en la lista (a menudo **abierto**).

- La tecla F2 activa la edición en contexto para la celda seleccionada actualmente.

## <a name="BKMK_PersistenceAndSavingSettings"></a> Persistencia y guardar la configuración

### <a name="overview"></a>Información general
 Aunque cada componente de software en Visual Studio es suele ser responsable de su propio estado y la persistencia, Visual Studio guarda la configuración en algunos casos, como con las posiciones y tamaños de ventana. En la tabla siguiente es una combinación de configuración que se guardan automáticamente y configuración que requieren un usuario explícito o programa la acción que se realizará.

|Object|Lo que se debe guardar|Cuándo se debe guardar|Dónde guardar|
|------------|------------------|------------------|-------------------|
|Objeto seleccionable (por ejemplo, una línea de código)|Un punto de interrupción en una línea de código<br /><br /> Un acceso directo de usuario asociado con la línea de código|Cuando se guarda el proyecto|El **opciones de usuario (.suo)** archivo del proyecto|
|Cuadro de diálogo|La ubicación del cuadro de diálogo, si se han movido<br /><br /> La vista que el usuario utilizó por última vez en el cuadro de diálogo|Cuando se cierra el cuadro de diálogo<br /><br /> Cuando finaliza la sesión de Visual Studio|En la memoria<br /><br /> Registro en **HKEY_Current_User**|
|Ventana|El tamaño y la ubicación de la ventana|Cuando se cierra la ventana<br /><br /> Cuando se cambia el modo de Visual Studio<br /><br /> Cuando finaliza la sesión de Visual Studio|El **opciones de usuario (.suo)** archivo del proyecto<br /><br /> Archivo de opciones personalizadas para la configuración de la ventana|
|Documento|La selección actual en el documento<br /><br /> La vista del documento<br /><br /> El último varios lugares, el usuario ha visitado|Cuando se guarda el documento|El **opciones de usuario (.suo)** archivo del proyecto|
|Proyecto|Referencias a archivos<br /><br /> Referencias a los directorios de disco<br /><br /> Referencias a otro software<br /><br /> Componentes<br /><br /> Información de estado sobre el propio proyecto|Cuando se guarda el proyecto|El archivo de proyecto|
|Soluciones|Referencias a proyectos<br /><br /> Referencias a archivos|Cuando se guarda el proyecto o solución|El **solución (.sln)** archivo|
|Configuración de **Herramientas > Opciones**|Personalizaciones del teclado<br /><br /> Personalizaciones de la barra de herramientas<br /><br /> Combinaciones de colores|Cuando el **Herramientas > opciones** cierra el cuadro de diálogo<br /><br /> Cuando finaliza la sesión de Visual Studio|Registro en **HKEY_Current_User**|

 ¿Qué está haciendo el usuario y al que hacen, determina si se guarda una configuración en memoria (durante la sesión), que se guardan en el disco (en las sesiones como una configuración del registro), como parte de la solución o proyecto propio archivo, como parte de la **solución Opciones (.suo)** de archivos o como una configuración personalizada de archivos ese componente de software que solo conoce. La tabla anterior muestra en el que se puede guardar la configuración de varios eventos. Sin embargo, existen otras ocasiones en que desea guardar el estado:

- Cuando el usuario cambia la ubicación dentro de un cuadro de diálogo o ventana

- Cuando el usuario transfiere el foco a otra ventana

- Cuando el usuario cambia de diseño a modo de depuración

- Cuando el usuario cierra sesión su cuenta

- Cuando se pasa a hibernación o se apaga el equipo

- Cuando el disco duro o de equipo está a punto de ser volver a formatear y volver a configurar

### <a name="window-configurations"></a>Configuraciones de ventana
 Una configuración de ventana es la presentación del entorno de desarrollo básica: es un esquema que consta de la lista de ventanas de herramientas está presentes y la manera en que se organizan. Para windows administrados por el IDE (windows IDE), información de diseño se conserva por usuario, por lo que cuando un usuario inicie el IDE, el diseño de ventana aparece igual que cuando últimos cerró Visual Studio. El estado y la posición de las ventanas del IDE se almacenan en un archivo de opciones personalizada en formato XML. Ventanas de herramientas que se crean mediante los paquetes que se cargan en el IDE de conservan su información de estado en el registro y pueden o no pueden ser por usuario.

#### <a name="profile-specific-layouts"></a>Diseños de perfil específicos
 Cada perfil incluye los diseños de ventana de herramienta, organizados en una manera familiar para las personas específicas para desarrolladores (los desarrolladores de Visual C++ esperan ver el **el Explorador de soluciones** en el lado izquierdo del IDE, mientras que los desarrolladores de C# esperan ver el  **El Explorador de soluciones** a la derecha). Después de que el usuario elija un perfil de inicio, se cargan los diseños de ventana específica del perfil. Un autor del paquete debe determinar el diseño de ventana más adecuado para la experiencia del cliente, sabiendo que, a continuación, se conservarán los cambios que realiza el usuario a la configuración de la ventana.

## <a name="BKMK_TouchInput"></a> Entrada táctil
 Los usuarios utilizan cada vez más productos de desarrollo de Microsoft en los dispositivos táctiles. Sin embargo, existen obstáculos que hacen que sea difícil utilizar herramientas de desarrollo en los dispositivos táctiles. Los usuarios esperan nuestros productos para ofrecer una experiencia táctil precisas y confiables. Es la intención de estas directrices informar a las decisiones sobre qué funciones táctiles para incorporar y animar a una experiencia táctil coherente a través de Visual Studio y otros productos relacionados.

### <a name="levels-of-experience"></a>Niveles de experiencia
 Los siguientes niveles de experiencia están diseñados para servir como guía para ayudar a los equipos a decidir qué funciones táctiles para ofrecer según su nivel deseado de interés de la inversión en contacto con usted.

- El **experiencia básica** es para equipos que desean proporcionar touch capacidades, por lo que no hay ningún callejones a lo largo de su trabajo.

- El **optimizado experiencia** es para equipos que desean proporcionar más capacidades de toque comunes (por ejemplo, los que suelen estar disponibles en las aplicaciones del explorador de internet).

- El **elevados experiencia** es para los equipos que desean agregar capacidades tales como gestos u otras funcionalidades opcionales que pueden hacer que su aplicación táctiles descriptivo.

||Experiencia básica|Experiencia optimizada|Experiencia con privilegios elevados|
|-|----------------------|--------------------------|-------------------------|
|Permite a los usuarios...|Corregir el código y solución/proyecto de nivel de lectura sin callejones|Realizar tareas de mantenimiento, refactorizaciones y navegación|Trabajar en una experiencia coherente, fluida e intuitiva con confianza|
|Editor|Movimiento panorámico y selección<br /><br /> Barra de desplazamiento táctil para saltar y presione + arrastrar|Acercar el zoom<br /><br /> Desplazamiento rápido<br /><br /> Selección<br /><br /> Fácil usar del menú contextual||
|Ventanas de herramientas superior|Movimiento panorámico de la lista<br /><br /> Selección de elementos<br /><br /> Barra de desplazamiento táctil para saltar y presione + arrastrar|Elemento fácil desplazamiento y la selección||
|Basado en ventanas||Cambiar el tamaño de ventana<br /><br /> Acceso rápido||
|Cuadro de documento||Facilitan la navegación entre archivos abiertos||
|Gestos||Asegúrese de gestos comunes funcionan en el IDE|Acciones de gesto<br /><br /> Compatibilidad con arrastrar y colocar y diseñadores|
|Otras consideraciones|||Teclado en pantalla personalizado|

#### <a name="gestures"></a>Gestos
 Gestos de proporcionan a los usuarios un acceso directo a los comandos que en caso contrario, es posible que requieren una interacción más complicada. Consulte las instrucciones de Windows en [gestos de toque comunes para aplicaciones de escritorio](http://msdn.microsoft.com/library/windows/desktop/dd940543\(v=vs.85\).aspx)y siga estas instrucciones para la mayoría los gestos, incluidos los movimientos simples como movimiento panorámico y zoom.
