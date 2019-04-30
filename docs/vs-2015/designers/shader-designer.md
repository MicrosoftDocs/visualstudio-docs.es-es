---
title: Diseñador de sombras | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 00b3a24e2e10672a2f25fdf42a3993f75c378c86
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432582"
---
# <a name="shader-designer"></a>Diseñador de sombras
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se describe cómo trabajar con el Diseñador de sombras de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear, modificar y exportar efectos visuales personalizados conocidos como *sombreadores*.  
  
 El Diseñador de sombras se puede usar para crear efectos visuales personalizados para un juego o aplicación, incluso sin conocer la programación con HLSL. Para crear un sombreador en el Diseñador de sombras, solo hay que diseñarlo como un gráfico, es decir, agregar a la superficie de diseño *nodos* que representan los datos y las operaciones y, después, establecer conexiones entre ellos para definir el modo en que las operaciones procesan los datos. En cada nodo de operación, se proporciona una vista previa del efecto hasta ese punto para que se pueda visualizar el resultado. Los datos fluyen a través de los nodos hacia un nodo final que representa la salida del sombreador.  
  
## <a name="supported-formats"></a>Formatos compatibles  
 El Diseñador de sombras admite estos formatos de sombreador:  
  
|Nombre de formato|Extensión de archivo|Operaciones admitidas (ver, editar, exportar)|  
|-----------------|--------------------|-------------------------------------------------|  
|Lenguaje de sombreador de gráfico dirigido|.dgsl|Ver, Editar|  
|Sombreador HLSL (código fuente)|.hlsl|Exportar|  
|Sombreador HLSL (código de bytes)|.cso|Exportar|  
|Encabezado de C++ (matriz de código de bytes HLSL)|.h|Exportar|  
  
## <a name="getting-started"></a>Introducción  
 En esta sección se describe cómo agregar un sombreador DGSL al proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y se ofrece la información básica necesaria para comenzar.  
  
#### <a name="to-add-a-dgsl-shader-to-your-project"></a>Para agregar un sombreador DGSL al proyecto  
  
1. En el **Explorador de soluciones**, abra el menú contextual del proyecto al que quiera agregar el sombreador y, después, elija **Agregar**, **Nuevo elemento**.  
  
2. En el cuadro de diálogo **Agregar nuevo elemento** en **Instalado**, seleccione **Gráficos**, y después seleccione **Gráfico de sombreador visual (.dgsl)**.  
  
3. Especifique el **Nombre** del archivo de sombreador y la **Ubicación** donde quiere que se cree.  
  
4. Elija el botón de **Agregar** .  
  
### <a name="the-default-shader"></a>El sombreador predeterminado  
 Cada vez que se crea un sombreador DGSL, comienza como un sombreador mínimo que solo tiene un nodo **Color de punto** que está conectado al nodo **Color final**. Aunque este sombreador sea completo y funcional, no hace mucho. Por tanto, el primer paso para crear un sombreador que funcione suele ser eliminar el nodo **Color de punto** o desconectarlo del nodo **Color final** para dejar espacio para otros nodos.  
  
## <a name="working-with-the-shader-designer"></a>Trabajar con el Diseñador de sombras  
 En las secciones siguientes se describe cómo usar el Diseñador de sombras para trabajar con sombreadores personalizados.  
  
### <a name="shader-designer-toolbars"></a>Barras de herramientas del Diseñador de sombras  
 Las barras de herramientas del Diseñador de sombras contienen comandos para trabajar con gráficos de sombreador DGSL.  
  
 Los comandos que afectan al estado del Diseñador de sombras se encuentran en la barra de herramientas **Modo Diseñador de sombras** en la ventana principal de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Las herramientas y los comandos de diseño se encuentran en la barra de herramientas **Diseñador de sombras** en la superficie de diseño del Diseñador de sombras.  
  
 Esta es la barra de herramientas **Modo Diseñador de sombras**:  
  
 ![La barra de herramientas Modo Diseñador de sombras.](../designers/media/digit-dsd-modal-toolbar.png "Digit-DSD-Modal-Toolbar")  
  
 En esta tabla se describen los elementos de la barra de herramientas **Modo Diseñador de sombras** que se muestran en el orden en que aparecen de izquierda a derecha:  
  
|Elemento de la barra de herramientas|Descripción|  
|------------------|-----------------|  
|**Seleccionar**|Permite la interacción con nodos y bordes en el gráfico. En este modo, puede seleccionar nodos y moverlos o eliminarlos, y puede establecer bordes o interrumpirlos.|  
|**Movimiento panorámico**|Habilita el movimiento de un gráfico de sombreador en relación con el marco de la ventana. Para realizar el movimiento panorámico, seleccione un punto en la superficie de diseño y muévalo.<br /><br /> En el modo **Seleccionar**, presione y mantenga presionada la tecla Ctrl para activar el modo **Movimiento panorámico** temporalmente.|  
|**Zoom**|Habilita la presentación de más o menos detalles de gráfico de sombreador en relación con el marco de la ventana. En el modo **Zoom**, seleccione un punto en la superficie de diseño y muévalo a la derecha o hacia abajo para acercar, o a la izquierda o hacia arriba para alejar.<br /><br /> En el modo **Seleccionar**, puede acercar o alejar con la rueda del mouse mientras presiona y mantiene presionada la tecla Ctrl.|  
|**Ajustar al tamaño**|Muestra el gráfico de sombreador completo en el marco de ventana.|  
|**Modo de representación en tiempo real**|Cuando se habilita la representación en tiempo real, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dibuja de nuevo la superficie de diseño, incluso si no se lleva a cabo ninguna acción de usuario. Este modo es útil cuando se trabaja con los sombreadores que cambian con el tiempo.|  
|**Vista previa con esfera**|Cuando está habilitada, se usa un modelo de una esfera para obtener una vista previa del sombreador. Solo se puede habilitar una forma de vista preliminar a la vez.|  
|**Vista previa con cubo**|Cuando está habilitada, se usa un modelo de un cubo para obtener una vista previa del sombreador. Solo se puede habilitar una forma de vista preliminar a la vez.|  
|**Vista previa con cilindro**|Cuando está habilitada, se usa un modelo de un cilindro para obtener una vista previa del sombreador. Solo se puede habilitar una forma de vista preliminar a la vez.|  
|**Vista previa con cono**|Cuando está habilitada, se usa un modelo de un cono para obtener una vista previa del sombreador. Solo se puede habilitar una forma de vista preliminar a la vez.|  
|**Vista previa con tetera**|Cuando está habilitada, se usa un modelo de una tetera para obtener una vista previa del sombreador. Solo se puede habilitar una forma de vista preliminar a la vez.|  
|**Vista previa con plano**|Cuando está habilitada, se usa un modelo de un plano para obtener una vista previa del sombreador. Solo se puede habilitar una forma de vista preliminar a la vez.|  
|**Cuadro de herramientas**|Muestra u oculta alternativamente el **Cuadro de herramientas**.|  
|**Propiedades**|Muestra u oculta alternativamente la ventana **Propiedades**.|  
|**Avanzadas**|Contiene comandos y opciones avanzados.<br /><br /> **Exportar**: Permite la exportación de un sombreador en varios formatos.<br /><br /> **Exportar como**: Exporta el sombreador como código fuente HLSL o como código de bytes del sombreador compilado. Para obtener más información sobre cómo exportar sombreadores, vea [Cómo: Exportar un sombreador](../designers/how-to-export-a-shader.md).<br /><br /> **Motores gráficos**: Permite la selección del representador que se usa para mostrar la superficie de diseño.<br /><br /> **Representar con D3D11**: Usa Direct3D 11 para representar la superficie de diseño de Diseñador de sombras.<br /><br /> **Representar con D3D11WARP**: Usa Windows Advanced Rasterization Platform (WARP) de Direct3D 11 para representar la superficie de diseño de Diseñador de sombras.<br /><br /> **Vista**: Permite seleccionar información adicional sobre Diseñador de sombras.<br /><br /> **Velocidad de fotogramas**: Cuando se habilita, muestra la velocidad de fotogramas actual en la esquina superior derecha de la superficie de diseño. La velocidad de fotogramas es el número de fotogramas dibujados por segundo.  Esta opción es útil cuando se habilita la opción **Modo de representación en tiempo real**.|  
  
> [!TIP]
> Puede hacer clic en el botón **Avanzadas** para volver a ejecutar el último comando.  
  
### <a name="working-with-nodes-and-connections"></a>Trabajar con nodos y conexiones  
 Use el modo **Seleccionar** para agregar, quitar, cambiar de posición, conectar y configurar los nodos. Aquí se muestra cómo realizar estas operaciones básicas:  
  
##### <a name="to-perform-basic-operations-in-select-mode"></a>Para realizar operaciones básicas en el modo Seleccionar  
  
- Esta es la manera de hacerlo:  
  
    - Para agregar un nodo al gráfico, selecciónelo en el **Cuadro de herramientas** y después muévalo a la superficie de diseño.  
  
    - Para quitar un nodo del gráfico, selecciónelo y después presione Supr.  
  
    - Para cambiar la posición de un nodo, selecciónelo y después muévalo a una nueva ubicación.  
  
    - Para conectar dos nodos, mueva un terminal de salida de un nodo a un terminal de entrada del otro nodo. Solo se pueden conectar los terminales que tienen tipos compatibles. Una línea entre los terminales muestra la conexión.  
  
    - Para quitar una conexión, en el menú contextual de uno de los terminales conectados, seleccione **Interrumpir vínculos**.  
  
    - Para configurar las propiedades de un nodo, seleccione el nodo y, después, en la ventana **Propiedades**, especifique los nuevos valores para las propiedades.  
  
### <a name="previewing-shaders"></a>Vista previa de sombreadores  
 Para ayudarle a entender cómo aparecerá un sombreador en la aplicación, puede configurar cómo se muestra una vista previa del efecto. Para aproximarse a la aplicación, puede elegir una de varias formas para representar, configurar las texturas y otros parámetros de material, habilitar la animación de efectos basados en tiempo y examinar la vista previa desde distintos ángulos.  
  
#### <a name="shapes"></a>Formas  
 El Diseñador de sombras incluye seis formas: una esfera, un cubo, un cilindro, un cono, una tetera y un plano, que puede usar para obtener una vista previa del sombreador. Dependiendo del sombreador, es posible que ciertas formas proporcionen una vista previa mejor.  
  
###### <a name="to-choose-a-preview-shape"></a>Para elegir una forma de vista previa  
  
- En la barra de herramientas **Modos del Diseñador de sombras**, seleccione la forma que quiera.  
  
#### <a name="WWS_MaterialParameters"></a> Texturas y parámetros de material  
 Muchos sombreadores dependen de texturas y propiedades de material para producir una apariencia única para cada tipo de objeto en la aplicación. Para ver qué aspecto tendrá el sombreador en la aplicación, puede establecer las texturas y las propiedades de material que se usan para representar la vista previa para que coincida con las texturas y los parámetros que es posible que use en la aplicación.  
  
###### <a name="to-bind-a-different-texture-to-a-texture-register-or-to-modify-other-material-parameters"></a>Para enlazar una textura distinta a un registro de textura o para modificar otros parámetros de material  
  
1. En el modo **Seleccionar**, seleccione un área vacía en la superficie de diseño. Esto hace que la ventana **Propiedades** muestre las propiedades globales de sombreador.  
  
2. En la ventana **Propiedades**, especifique los nuevos valores para las propiedades de textura y parámetro que quiere cambiar.  
  
   Estos son los parámetros de sombreador que se pueden modificar:  
  
|Parámetro|Propiedades|  
|---------------|----------------|  
|**Textura 1** – **Textura 8**|**Acceso**:                             **Público** para que esta propiedad se pueda establecer desde el Editor de modelos. De lo contrario, **Privado**.<br /><br /> **Nombre de archivo**: Ruta de acceso completa del archivo de textura asociado al registro de textura.|  
|**Color ambiental de material**|**Acceso**:                             **Público** para que esta propiedad se pueda establecer desde el Editor de modelos. De lo contrario, **Privado**.<br /><br /> **Valor**: El color difuso del píxel actual debido a la iluminación indirecta o ambiente:.|  
|**Color difuso de material**|**Acceso**: **Público** para que esta propiedad se pueda establecer desde el Editor de modelos. De lo contrario, **Privado**.<br /><br /> **Valor**:  Un color que describe cómo difumina la iluminación directa el píxel actual.|  
|**Color emisor de luz de material**|**Acceso**:                              **Público** para que esta propiedad se pueda establecer desde el Editor de modelos. De lo contrario, **Privado**.<br /><br /> **Valor**: Contribución de color del píxel actual debida a la iluminación propia proporcionada.|  
|**Reflexión especular de material**|**Acceso**:                              **Público** para que esta propiedad se pueda establecer desde el Editor de modelos. De lo contrario, **Privado**.<br /><br /> **Valor**: Un color que describe cómo refleja la iluminación directa el píxel actual.|  
|**Potencia especular de material**|**Acceso**:                             **Público** para que esta propiedad se pueda establecer desde el Editor de modelos. De lo contrario, **Privado**.<br /><br /> **Valor**: El exponente que define la intensidad de los reflejos especulares en el píxel actual.|  
  
#### <a name="time-based-effects"></a>Efectos basados en tiempo  
 Algunos sombreadores tienen un componente basado en tiempo que anima el efecto. Para mostrar el aspecto que tiene el efecto en acción, es necesario actualizar la vista previa varias veces por segundo. De forma predeterminada, la vista previa solo se actualiza cuando se cambia el sombreador. Para cambiar este comportamiento y poder ver los efectos basados en tiempo, tendrá que habilitar la representación en tiempo real.  
  
###### <a name="to-enable-real-time-rendering"></a>Para habilitar la representación en tiempo real  
  
- En la barra de herramientas del Diseñador de sombras, seleccione **Representación en tiempo real**.  
  
#### <a name="examining-the-effect"></a>Examinar el efecto  
 Muchos sombreadores se ven afectados por variables como el ángulo de visualización o la iluminación direccional. Para examinar cómo responde el efecto cuando se cambian estas variables, puede girar libremente la forma de vista previa y observar cómo se comporta el sombreador.  
  
###### <a name="to-rotate-the-shape"></a>Para girar la forma  
  
- Mantenga presionada la tecla Alt y, después, seleccione cualquier punto de la superficie de diseño y muévalo.  
  
### <a name="exporting-shaders"></a>Exportar sombreadores  
 Antes de poder usar un sombreador en la aplicación, tendrá que exportar en un formato que DirectX entienda.  
  
 Puede exportar sombreadores como código fuente de HLSL o como código de bytes compilado del sombreador. El código fuente de HLSL se exporta a un archivo de texto que tiene la extensión de nombre de archivo .hlsl. El código de bytes de sombreador se puede exportar a un archivo binario sin formato que tiene la extensión de nombre de archivo .cso o a un archivo de encabezado (.h) de C++ que codifica el código de bytes del sombreador en una matriz.  
  
 Para obtener más información sobre cómo exportar sombreadores, vea [Cómo: Exportar un sombreador](../designers/how-to-export-a-shader.md).  
  
## <a name="keyboard-shortcuts"></a>Métodos abreviados de teclado  
  
|Comando|Métodos abreviados de teclado|  
|-------------|------------------------|  
|Cambiar al modo **Seleccionar**|Ctrl+G, Ctrl+Q<br /><br /> S|  
|Cambiar al modo **Zoom**|Ctrl+G, Ctrl+Z<br /><br /> Z|  
|Cambiar al modo **Movimiento panorámico**|Ctrl+G, Ctrl+P<br /><br /> K|  
|Seleccionar todo|Ctrl+A|  
|Eliminar la selección actual|Eliminar|  
|Cancelar la selección actual|Escape|  
|Acercar|Ctrl+rueda del mouse hacia delante<br /><br /> Signo más (+)|  
|Alejar|Ctrl+rueda del mouse hacia atrás<br /><br /> Signo menos (-)|  
|Movimiento panorámico hacia arriba de la superficie de diseño|Rueda del mouse hacia atrás<br /><br /> AvPág|  
|Movimiento panorámico hacia abajo de la superficie de diseño|Rueda del mouse hacia delante<br /><br /> RePág|  
|Movimiento panorámico hacia la izquierda de la superficie de diseño|Mayús+rueda del mouse hacia atrás<br /><br /> Rueda del mouse a la izquierda<br /><br /> Mayús+AvPág|  
|Movimiento panorámico hacia la derecha de la superficie de diseño|Mayús+rueda del mouse hacia delante<br /><br /> Rueda del mouse a la derecha<br /><br /> Mayús+RePág|  
|Mover el foco del teclado a otro nodo|Las teclas de dirección|  
|Seleccionar el nodo que tiene el foco del teclado (agrega el nodo al grupo de selección)|Mayús+Barra espaciadora|  
|Alternar la selección del nodo que tiene el foco del teclado|Ctrl+Barra espaciadora|  
|Alternar la selección actual (si no se selecciona ningún nodo, seleccionar el nodo que tiene el foco del teclado)|Barra espaciadora|  
|Mover la selección actual hacia arriba|Mayús+Flecha arriba|  
|Mover la selección actual hacia abajo|Mayús+Flecha abajo|  
|Mover la selección actual hacia la izquierda|Mayús+Flecha izquierda|  
|Mover la selección actual hacia la derecha|Mayús+Flecha derecha|  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Trabajar con activos 3D para juegos y aplicaciones](../designers/working-with-3-d-assets-for-games-and-apps.md)|Proporciona información general sobre las herramientas de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que se pueden usar para trabajar con texturas e imágenes, modelos 3D y efectos de sombreador.|  
|[Editor de imágenes](../designers/image-editor.md)|Describe cómo usar el editor de imágenes de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para trabajar con texturas e imágenes.|  
|[Editor de modelos](../designers/model-editor.md)|Describe cómo usar el Editor de modelos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para trabajar con modelos 3D.|
