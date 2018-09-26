---
title: Editor de imágenes
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ed7c1ec10b6cc6b2eac450ea33beceaaf58bc06
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029126"
---
# <a name="image-editor"></a>Editor de imágenes

En este artículo se describe cómo trabajar con el **Editor de imágenes** de Visual Studio para ver y modificar recursos de textura e imagen.

Puede usar el **Editor de imágenes** para trabajar con los tipos de formato de imagen y textura enriquecidos que se usan en el desarrollo de aplicaciones de DirectX. Esto incluye compatibilidad con formatos de archivo de imagen populares y codificaciones de color, características como canales alfa y asignación de MIP y muchos de los formatos de textura muy comprimidos y acelerados por hardware que son compatibles con DirectX.

## <a name="supported-formats"></a>Formatos compatibles

El **Editor de imágenes** admite estos formatos de imagen:

|Nombre de formato|Extensión de nombre de archivo|
|-----------------|-------------------------|
|Formato PNG (Portable Network Graphics)|*.png*|
|JPEG|*.jpg*, *.jpeg*, *.jpe*, *.jfif*|
|DirectDraw Surface|*.dds*|
|Formato de intercambio de gráficos|*.gif*|
|Bitmap|*.bmp*, *.dib*|
|Tagged Image File Format|*.tif*, *.tiff*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>Primeros pasos

En esta sección se describe cómo agregar una imagen al proyecto Visual Studio y configurarla de acuerdo con sus requisitos.

### <a name="add-an-image-to-your-project"></a>Agregar una imagen al proyecto

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto al que quiere agregar la imagen y, después, elija **Agregar** > **Nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento**, en **Instalado**, seleccione **Gráficos** y, después, seleccione un formato de archivo apropiado para la imagen.

   > [!NOTE]
   > Si no ve la categoría **Gráficos** en el cuadro de diálogo **Agregar nuevo elemento**, es posible que deba instalar el componente **Editores de imágenes y modelos 3D**. Cierre el cuadro de diálogo y seleccione **Herramientas** > **Obtener herramientas y características** en la barra de menús, para abrir el **Instalador de Visual Studio**. Seleccione la pestaña **Componentes individuales** y, después, seleccione el componente **Editores de imágenes y modelos 3D** en la categoría **Juegos y gráficos**. Seleccione **Modificar**.
   >
   > ![Componente Editores de imágenes y modelos 3D](media/image-3d-model-editors-component.png)

   Para obtener información sobre cómo elegir un formato de archivo según sus requisitos, vea [Choose the image format](#choose-the-image-format) (Elegir el formato de archivo).

3. Especifique el **Nombre** del archivo de imagen y la **Ubicación** en la que quiera que se cree.

4. Elija el botón de **Agregar** .

### <a name="choose-the-image-format"></a>Elegir el formato de imagen

Según cómo piense utilizar la imagen, determinados formatos de archivo pueden ser más adecuados que otros. Por ejemplo, es posible que algunos formatos no admitan una característica que necesite como, por ejemplo, la transparencia o un formato de color concreto. Puede que algunos formatos no proporcionen una compresión adecuada para el tipo de contenido de imagen que ha planeado.

Con la información siguiente podrá elegir un formato de imagen que satisfaga sus necesidades:

**Imagen de mapa de bits (.bmp)**

Formato de la imagen de mapa de bits. Un formato de imagen sin comprimir que admite color de 24 bits. El formato de mapa de bits no admite transparencias.

**Imagen GIF (.gif)**

Formato de imagen de formato de intercambio de gráficos (GIF). Un formato de imagen con compresión LZW, y sin pérdida de datos, que admite hasta 256 colores. No es adecuado para fotografías e imágenes que tienen una gran cantidad de detalle de color, pero proporciona buenas razones de compresión para las imágenes con poco color que tienen un alto grado de coherencia de color.

**Imagen JPG (.jpg)**

Formato de imagen Joint Photographic Experts Group (JPEG). Un formato de imagen muy comprimido, con pérdida de datos, que admite color de 24 bits y es adecuado para la compresión de uso general de las imágenes que tienen un alto grado de coherencia de color.

**Imagen PNG (.png)**

Formato de imagen Portable Network Graphics (PNG). Un formato de imagen con compresión moderada, y sin pérdida de datos, que admite color de 24 bits y transparencia alfa. Es adecuado para imágenes naturales y artificiales, pero no proporciona razones de compresión tan buenas como los formatos con pérdida de datos como JPG o GIF.

**Imagen TIFF (.tif)**

Formato de imagen Tagged Image File Format (TIFF o TIF). Un formato de imagen flexible que admite varios esquemas de compresión.

**Textura DDS (.dds)**

Formato de textura de DirectDraw Surface (DDS). Un formato de textura muy comprimido y con pérdida de datos, que admite color de 24 bits y transparencia alfa. Los valores de las razones de compresión pueden ser tan altos como 8:1. Se basa en la compresión de textura S3, que se puede descomprimir en hardware gráfico.

**Imagen TGA (.tga)**

El formato de imagen Truevision Graphics Adapter (TGA) (también conocido como Targa). Un formato de imagen con compresión RLE, y sin pérdida de datos, que admite tanto imágenes con asignación de colores (paleta de colores) o con color directo de hasta 24 bits como transparencia alfa. No es adecuado para fotografías e imágenes que tienen una gran cantidad de detalle de color, pero proporciona buenas razones de compresión para las imágenes que tienen intervalos largos de colores idénticos.

### <a name="configure-the-image"></a>Configurar la imagen

Antes de empezar a trabajar con la imagen que ha creado, puede cambiar su configuración predeterminada. Por ejemplo, puede cambiar sus dimensiones o el formato de color que utiliza. Para obtener información sobre cómo configurar estas y otras propiedades de imagen, consulte [Propiedades de imagen](#image-properties).

> [!NOTE]
> Antes de guardar el trabajo, asegúrese de establecer la propiedad **Formato de color** si quiere utilizar un formato de color concreto. Si el formato de archivo admite la compresión, puede ajustar los valores de compresión al guardar el archivo por primera vez o cuando elija **Guardar como**.

## <a name="work-with-the-image-editor"></a>Trabajar con el Editor de imágenes

En esta sección se describe cómo utilizar el **Editor de imágenes** para modificar texturas e imágenes.

Los comandos que influyen en el estado del **Editor de imágenes** se encuentran en la barra de herramientas **Modo Editor de imágenes** junto con los comandos avanzados. La barra de herramientas se encuentra en el borde superior de la superficie de diseño del **Editor de imágenes**. Las herramientas de dibujo se encuentran en la barra de herramientas del **Editor de imágenes** a lo largo del borde izquierdo de la superficie de diseño del **Editor de imágenes**.

### <a name="image-editor-mode-toolbar"></a>Barra de herramientas Modo Editor de imágenes

![Barra de herramientas Modo Editor de imágenes en Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

En esta tabla se describen los elementos de la barra de herramientas **Modo Editor de imágenes** y se muestran en el orden en que aparecen de izquierda a derecha:

|Elemento de la barra de herramientas|Descripción|
|------------------|-----------------|
|**Seleccionar**|Permite seleccionar una región rectangular de una imagen. Después de seleccionar una región, la puede cortar, copiar, mover, escalar, girar, voltear o eliminar. Cuando hay una selección activa, las herramientas de dibujo solo afectan a la región seleccionada.|
|**Selección irregular**|Permite seleccionar una región irregular de una imagen. Después de seleccionar una región, la puede cortar, copiar, mover, escalar, girar, voltear o eliminar. Cuando hay una selección activa, las herramientas de dibujo solo afectan a la región seleccionada.|
|**Selección de varita**|Permite seleccionar una región de color similar de una imagen. La *tolerancia*, es decir, la diferencia máxima entre colores adyacentes considerados similares, puede configurarse para incluir un rango mayor o menor de colores similares. Después de seleccionar una región, la puede cortar, copiar, mover, escalar, girar, voltear o eliminar. Cuando hay una selección activa, las herramientas de dibujo solo afectan a la región seleccionada.|
|**Movimiento panorámico**|Permite mover la imagen con relación al marco de la ventana. En el modo **Movimiento panorámico**, seleccione un punto de la imagen y, después, muévalo alrededor.<br /><br /> Para activar temporalmente el modo **Movimiento panorámico**, mantenga presionada la tecla **Ctrl**.|
|**Zoom**|Permite presentar más o menos detalles de la imagen con relación al marco de la ventana. En el modo **Zoom**, seleccione un punto de la imagen y muévalo a la derecha o hacia abajo para acercar, o a la izquierda o hacia arriba para alejar.<br /><br /> Para acercar o alejar, mantenga presionada la tecla **Ctrl** mientras usa la rueda del mouse o presiona el signo más (**+**) o el signo menos (**-**).|
|**Ajustar el zoom al tamaño real**|Muestra la imagen mediante una relación 1:1 entre los píxeles de la imagen y los píxeles de la pantalla.|
|**Ajustar el zoom al tamaño completo**|Muestra la imagen completa en el marco de la ventana.|
|**Ajustar el zoom al ancho**|Muestra el ancho completo en el marco de la ventana.|
|**Grid**|Habilita o deshabilita la cuadrícula que muestra los límites de píxeles. Es posible que la cuadrícula no aparezca hasta que haga zoom en la imagen.|
|**Ver el nivel de MIP siguiente**|Activa el siguiente nivel de MIP más grande en una cadena de asignación de MIP. El nivel de MIP activo se muestra en la superficie de diseño. Este elemento solo está disponible para las texturas que tienen niveles de MIP.|
|**Ver el nivel de MIP anterior**|Activa el siguiente nivel de MIP más pequeño en una cadena de asignación de MIP. El nivel de MIP activo se muestra en la superficie de diseño. Este elemento solo está disponible para las texturas que tienen niveles de MIP.|
|**Canal rojo**<br /><br /> **Canal verde**<br /><br /> **Canal azul**<br /><br /> **Canal alfa**|Habilita o deshabilita el canal de colores concreto. **Nota**: Al habilitar o deshabilitar sistemáticamente los canales de color, puede aislar los problemas que están relacionados con uno o varios de ellos. Por ejemplo, puede identificar una transparencia alfa incorrecta.|
|**Fondo**|Habilita o deshabilita la presentación del fondo a través de las partes transparentes de la imagen. Puede elegir entre estas opciones para configurar cómo se muestra el fondo:<br /><br /> **Tablero**<br /> Utiliza un color verde junto con el color de fondo especificado para mostrar el fondo como un patrón de tablero. Puede usar esta opción para que las partes transparentes de la imagen sean más evidentes.<br /><br /> Fondo blanco<br /> Utiliza el color blanco para mostrar el fondo.<br /><br /> Fondo negro<br /> Utiliza el color negro para mostrar el fondo.<br /><br /> Fondo animado<br /> Gira lentamente el patrón de tablero. Puede usar esta opción para que las partes transparentes de la imagen sean más evidentes.|
|**Propiedades**|Abre o cierra alternativamente la ventana **Propiedades**.|
|**Avanzadas**|Contiene comandos y opciones adicionales.<br /><br /> **Filtros**<br /><br /> Proporciona varios filtros de imágenes habituales: **Blanco y negro**, **Desenfoque**, **Brillar**, **Oscurecer**, **Detección de bordes**, **Relieve**, **Invertir colores**, **Ripple**, **Tono sepia** y **Dar nitidez**.<br /><br /> **Motores gráficos**<br /><br /> **Representar con D3D11**<br /> Utiliza Direct3D 11 para representar la superficie de diseño del **Editor de imágenes**.<br /><br /> **Representar con D3D11WARP**<br /> Utiliza Windows Advanced Rasterization Platform (WARP) de Direct3D 11 para representar la superficie de diseño del **Editor de imágenes**.<br /><br /> **Herramientas**<br /><br /> **Voltear horizontalmente**<br /> Transpone la imagen alrededor de su eje horizontal, o x.<br /><br /> **Voltear verticalmente**<br /> Transpone la imagen alrededor de su eje vertical, o y.<br /><br /> **Generar MIP**<br /> Genera los niveles de MIP para una imagen. Si ya existen niveles de MIP, se vuelven a crear desde el nivel de MIP más grande. Se perderán los cambios realizados en los niveles de MIP más pequeños. Para guardar los niveles de MIP que ha generado, debe usar el formato *.dds* para guardar la imagen.<br /><br /> **Vista**<br /><br /> **Velocidad de fotogramas**<br /> Cuando esta opción está habilitada, muestra la velocidad de fotogramas en la esquina superior derecha de la superficie de diseño. La velocidad de fotogramas es el número de fotogramas dibujados por segundo. **Consejo**: Puede hacer clic en el botón **Avanzado** para volver a ejecutar el último comando.|

### <a name="image-editor-toolbar"></a>Barra de herramientas del Editor de imágenes

![Barra de herramientas del Editor de imágenes](../designers/media/digit-tre-toolbar.png)

En la tabla siguiente se describen los elementos de la barra de herramientas **Editor de imágenes**, en el orden en que aparecen de arriba abajo:

|Elemento de la barra de herramientas|Descripción|
|------------------|-----------------|
|**Lápiz**|Utiliza la selección de color activa para dibujar el trazo de un alias. Puede establecer el color y el grosor del trazo en la ventana **Propiedades**.|
|**Pincel**|Utiliza la selección de color activa para dibujar un trazo suavizado. Puede establecer el color y el grosor del trazo en la ventana **Propiedades**.|
|**Aerógrafo**|Utiliza la selección de color activa para dibujar un trazo suavizado que se combina con la imagen y se vuelve más saturado como una función de tiempo. Puede establecer el color y el grosor del trazo en la ventana **Propiedades**.|
|**Cuentagotas**|Establece la selección de color activo en el color del píxel seleccionado.|
|**Relleno**|Utiliza la selección de color activa para rellenar una región de la imagen. La región afectada se define como el píxel en el que se aplica el relleno, junto con todos los píxeles que están conectados a ella mediante píxeles del mismo color y que es el mismo color en sí. Si el relleno se aplica en una selección activa, la selección restringe la región afectada.<br /><br /> De forma predeterminada, la selección de color activa se combina con la región afectada de la imagen en función de su componente alfa. Para utilizar la selección de color activa para sobrescribir la región afectada, mantenga presionada la tecla **Mayús** al usar la herramienta de relleno.|
|**Borrador**|Establece los píxeles en el color totalmente transparente si la imagen admite un canal alfa. En caso contrario, los establece en el color de fondo activo.|
|**Línea**, **Rectángulo**, **Rectángulo redondeado**, **Elipse**|Dibuja una forma en la imagen. Puede establecer el color y el grosor del esquema en la ventana **Propiedades**.<br /><br /> Para dibujar una primitiva que tenga el mismo ancho y alto, mantenga presionada la tecla **Mayús** mientras dibuja.|
|**Texto**|Utiliza la selección de color de primer plano para dibujar texto. La selección de color de fondo determina el color de fondo. Para un fondo transparente, el valor alfa de la selección de color de fondo debe ser 0. Cuando la región de texto esté activa, puede establecer si el texto se dibuja con un trazo suavizado, así como el **Valor**, la **Fuente** y el **Tamaño** del texto, además del estilo (**Negrita**, **Cursiva** o **Subrayado**), en la ventana **Propiedades**. El contenido y la apariencia del texto finalizan cuando la región de texto ya no está activa.|
|**Girar**|Gira la imagen 90 grados en el sentido de las agujas del reloj.|
|**Recortar**|Recorta la imagen al tamaño de la selección activa.|

### <a name="work-with-mip-levels"></a>Trabajar con niveles de MIP

Algunos formatos de imagen, como DirectDraw Surface (*.dds*), admiten niveles de MIP con nivel de detalle (LOD) del espacio de textura. Para obtener información sobre cómo generar y trabajar con niveles de MIP, vea [Cómo: Crear y modificar niveles de MIP](../designers/how-to-create-and-modify-mip-levels.md).

### <a name="work-with-transparency"></a>Trabajar con transparencia

Algunos formatos de imagen, como DirectDraw Surface (*.dds*), admiten la transparencia. La transparencia se puede utilizar de varias maneras, según la herramienta que use. Para especificar el nivel de transparencia de una selección de color, en la ventana **Propiedades**, establezca el componente **A** (alfa) de la selección de color.

En esta table se describen el modo en que diferentes tipos de herramientas controlan cómo se aplica la transparencia:

|Herramienta|Descripción|
|----------|-----------------|
|**Lápiz**, **Pincel**, **Aerógrafo**, **Línea**, **Rectángulo**, **Rectángulo redondeado**, **Elipse**, **Texto**|Para combinar la selección de color activa con la imagen, en la ventana **Propiedades**, expanda el grupo de propiedades **Canales**, establezca la casilla de verificación **Dibujar** en el canal  **Alfa** y, a continuación, dibuje normalmente.<br /><br /> Para dibujar con la selección de color activa y dejar el valor alfa de la imagen en su lugar, desactive la casilla de verificación **Dibujar** del canal **Alfa** y, después, dibuje normalmente.|
|**Relleno**|Para combinar la selección de color activa con la imagen, elija el área que se deba rellenar.<br /><br /> Para utilizar la selección de color activa, incluido el valor del canal alfa, para sobrescribir la imagen, mantenga presionada la tecla **Mayús** y, después, elija el área que se deba rellenar.|

### <a name="image-properties"></a>Propiedades de la imagen

Puede utilizar la ventana **Propiedades** para especificar distintas propiedades de la imagen. Por ejemplo, puede establecer las propiedades de ancho y alto para cambiar el tamaño de la imagen.

En la tabla siguiente se describen las propiedades de la imagen:

|Propiedad.|Descripción|
|--------------|-----------------|
|Ancho|El ancho de la imagen.|
|Alto|El alto de la imagen.|
|Bits por píxel|El número de bits que representan a cada píxel. El valor de esta propiedad depende del **Formato de color** de la imagen.|
|Selección transparente|Se establece como **true** para combinar la capa de selección con la imagen principal, según el valor alfa de la capa de selección; en caso contrario, se establece como **false**. Este elemento solo está disponible para las imágenes que admiten el valor alfa.|
|Formato|Formato de color de la imagen. Puede especificar varios formatos de color según el formato de imagen. El formato de color define el número y el tipo de canales de color que se incluyen en la imagen, así como el tamaño y la codificación de varios canales.|
|Nivel de MIP|Nivel de MIP activo. Este elemento solo está disponible para las texturas que tienen niveles de MIP.|
|Recuento de niveles de MIP|Número total de niveles de MIP de la imagen. Este elemento solo está disponible para las texturas que tienen niveles de MIP.|
|Recuento de fotogramas|Número total de fotogramas de la imagen. Este elemento solo está disponible para las imágenes que admiten matrices de textura.|
|Fotograma|Fotograma actual. Solo se puede ver el primer fotograma; todos los otros fotogramas se pierden al guardar la imagen.|
|Número de segmentos de profundidad|Número total de segmentos de profundidad de la imagen. Este elemento solo está disponible para las imágenes que admiten texturas de volumen.|
|Segmento de profundidad|Segmento de profundidad actual. Solo se puede ver el primer segmento; todos los otros segmentos se pierden al guardar la imagen.|

> [!NOTE]
> Dado que la propiedad **Girar** se aplica a todas las herramientas y regiones seleccionadas, siempre aparece en la parte inferior de la ventana **Propiedades** junto con otras propiedades de la herramienta. **Girar "x" grados** siempre se muestra porque toda la imagen se selecciona implícitamente cuando no hay ninguna otra selección o herramienta activa. Para obtener más información sobre la propiedad **Girar "x" grados**, vea [Propiedades de la herramienta](#tool -properties).

### <a name="resize-images"></a>Cambiar el tamaño de imágenes

Hay dos formas de cambiar el tamaño de una imagen. En ambos casos, el **Editor de imágenes** utiliza la interpolación bilineal para crear un nuevo muestreo de la imagen.

- En la ventana **Propiedades**, especifique nuevos valores para las propiedades **Ancho** y **Alto**.

- Seleccione toda la imagen y utilice los marcadores de borde para cambiar el tamaño de la imagen.

### <a name="selected-regions"></a>Regiones seleccionadas

Las selecciones en el **Editor de imágenes** definen las regiones de la imagen que están activas. Las regiones activas se ven afectadas por las herramientas y las transformaciones. Cuando hay una selección activa, las áreas fuera de la región seleccionada no se ven afectadas por la mayoría de herramientas y transformaciones. Si no hay ninguna selección activa, toda la imagen está activa.

La selección activa restringe o define la mayoría de las herramientas (**Lápiz**, **Pincel**, **Aerógrafo**, **Relleno**, **Borrador** y primitivas 2D) y transformaciones (**Girar**, **Recortar**, **Invertir colores**, **Voltear horizontalmente** y **Voltear verticalmente**). No obstante, algunas herramientas (**Eyedropper** y **Text**) y transformaciones (**Generar Mips**) no se ven afectadas por ninguna selección activa. Estas herramientas siempre se comportan como si toda la imagen fuera la selección activa.

Mientras está seleccionando una región, puede mantener presionada la tecla **Mayús** para realizar una selección proporcional (cuadrado). En caso contrario, la selección no está restringida.

#### <a name="resize-selections"></a>Cambiar tamaño de selección

Después de seleccionar una región, puede cambiar su tamaño o el contenido de la imagen; para ello, cambie el tamaño del marcador de la selección. Al cambiar el tamaño de la región seleccionada, puede usar las siguientes teclas modificadoras para cambiar el comportamiento de la región seleccionada mientras cambia su tamaño:

**Ctrl**: Copia el contenido de la región seleccionada antes de que cambie de tamaño. La imagen original queda intacta, mientras que el tamaño de la copia se cambia.

**Mayús**: Cambia el tamaño de la región seleccionada en proporción a su tamaño original.

**Alt**: Cambia el tamaño de la región de la selección. Esto deja la imagen sin modificar.

En la tabla siguiente se describen las combinaciones válidas de teclas modificadoras que devuelven:

|Ctrl|Shift|Alt|Descripción|
|----------|-----------|---------|-----------------|
||||Cambia el tamaño del contenido de la región seleccionada.|
||**Mayús**||Cambia proporcionalmente el tamaño del contenido de la región seleccionada.|
|||**Alt**|Cambia el tamaño de la región seleccionada. Esto define una nueva región de selección.|
||**Mayús**|**Alt**|Cambia proporcionalmente el tamaño de la región seleccionada. Esto define una nueva región de selección.|
|**Ctrl**|||Copia y después cambia el tamaño del contenido de la región seleccionada.|
|**Ctrl**|**Mayús**||Copia y después cambia proporcionalmente el tamaño del contenido de la región seleccionada.|

### <a name="tool-properties"></a>Propiedades de herramientas

Cuando está seleccionada una herramienta, puede utilizar la ventana **Propiedades** para especificar los detalles de cómo afecta a la imagen. Por ejemplo, puede establecer el grosor de la herramienta **Lápiz** o el color de la herramienta **Pincel**.

Puede establecer un color de primer plano y un color de fondo. Ambos admiten un canal alfa para proporcionar opacidad definida por el usuario. La configuración se aplica a todas las herramientas. Si utiliza un mouse, el botón izquierdo se corresponde con el color de primer plano, mientras que el botón derecho se corresponde con el color de fondo.

En la tabla siguiente se describen las propiedades de las herramientas:

|Herramienta|Propiedades|
|----------|----------------|
|Todas las herramientas y selecciones|**Girar "x" grados**<br /> Define la cantidad, en grados, que la selección o el efecto de la herramienta gira en el sentido de las agujas del reloj.|
|**Lápiz**, **Pincel**, **Aerógrafo**, **Borrador**|**Grosor**<br /> Define el tamaño del área que se ve afectada por la herramienta.|
|**Texto**|**Suavizado**<br /> Dibuja texto con bordes suavizados. Esto proporciona al texto una apariencia más suave.<br /><br /> **Valor**<br /> El texto que se debe dibujar.<br /><br /> **Fuente**<br /> La fuente utilizada para dibujar el texto.<br /><br /> **Size**<br /> El tamaño del texto.<br /><br /> **Negrita**<br /> Pone la fuente en negrita.<br /><br /> **Cursiva**<br /> Pone la fuente en cursiva.<br /><br /> **Subrayado**<br /> Pone la fuente subrayada.|
|**Primitiva 2D**|**Suavizado**<br /> Dibuja las primitivas que tienen bordes suavizados. Esto les proporciona una apariencia más suave.<br /><br /> **Grosor**<br /> Define el grosor de la línea que constituye el límite de la primitiva.<br /><br /> **Radio X**<br /> (Solo rectángulo redondeado) Define el radio de redondeo para los bordes superior e inferior de la primitiva.<br /><br /> **Radio Y**<br /> (Solo rectángulo redondeado) Define el radio de redondeo para los bordes izquierdo y derecho de la primitiva.|
|**Lápiz**, **Pincel**, **Aerógrafo**, **Primitiva 2D**|**Canales**<br /> Habilita o deshabilita canales de color concretos para ver y dibujar. Si se establece **Ver** para un canal de color concreto, ese canal está visible en la imagen; en caso contrario, no está visible. Si se establece **Dibujar** para un canal de color concreto, ese canal se ve afectado por las operaciones de dibujo; en caso contrario, esto no ocurre.|
|**Selección de varita**, **Relleno**|**Tolerancia**<br /> Define la diferencia máxima entre colores adyacentes considerados similares, de manera que menos o más colores similares se convierten en parte de la región afectada o seleccionada. De forma predeterminada, el valor es 32, lo que significa que los píxeles adyacentes con 32 tonalidades (más claras u oscuras) del color original se consideran parte de la región.|

## <a name="keyboard-shortcuts"></a>Métodos abreviados de teclado

|Comando|Métodos abreviados de teclado|
|-------------|------------------------|
|Cambiar al modo **Seleccionar**|**S**|
|Cambiar al modo **Zoom**|**Z**|
|Cambiar al modo **Movimiento panorámico**|**K**|
|Seleccionar todo|**Ctrl**+**A**|
|Eliminar la selección actual|**Eliminar**|
|Cancelar la selección actual|**Esc** (Escape)|
|Acercar|**Ctrl**+**Rueda del mouse hacia delante**<br /><br /> **Ctrl**+**RePág**<br /><br /> Signo más (**+**)|
|Alejar|**Ctrl**-**Rueda del mouse hacia atrás**<br /><br /> **Ctrl**-**AvPág**<br /><br /> Signo menos (**-**)|
|Aplicar a la imagen un movimiento panorámico hacia arriba|**Rueda del mouse hacia atrás**<br /><br /> **AvPág**|
|Aplicar a la imagen un movimiento panorámico hacia abajo|**Rueda del mouse hacia delante**<br /><br /> **RePág**|
|Aplicar a la imagen un movimiento panorámico hacia la izquierda|**Mayús**+**Rueda del mouse hacia atrás**<br /><br /> **Rueda del mouse a la izquierda**<br /><br /> **Mayús**+**AvPág**|
|Aplicar a la imagen un movimiento panorámico hacia la derecha|**Mayús**+**Rueda del mouse hacia delante**<br /><br /> **Rueda del mouse a la derecha**<br /><br /> **Mayús**+**RePág**|
|Ajustar el zoom al tamaño real|**Ctrl**+**0** (cero)|
|Ajustar la imagen a la ventana|**Ctrl**+**G**, **Ctrl**+**F**|
|Ajustar la imagen al ancho de la ventana|**Ctrl**+**G**, **Ctrl**+**I**|
|Alternar la cuadrícula|**Ctrl**+**G**, **Ctrl**+**G**|
|Recortar la imagen a la selección actual|**Ctrl**+**G**, **Ctrl**+**C**|
|Ver el nivel de MIP siguiente (mayor nivel de detalle)|**Ctrl**+**G**, **Ctrl**+**6**|
|Ver el nivel de MIP anterior (menor nivel de detalle)|**Ctrl**+**G**, **Ctrl**+**7**|
|Alternar el canal de color rojo|**Ctrl**+**G**, **Ctrl**+**1**|
|Alternar el canal de color verde|**Ctrl**+**G**, **Ctrl**+**2**|
|Alternar el canal de color azul|**Ctrl**+**G**, **Ctrl**+**3**|
|Alternar el canal alfa (transparencia)|**Ctrl**+**G**, **Ctrl**+**4**|
|Alternar el patrón de tablero alfa|**Ctrl**+**G**, **Ctrl**+**B**|
|Cambiar a la herramienta Selección irregular|**L**|
|Cambiar a la herramienta Selección de varita|**M**|
|Cambiar a la herramienta Lápiz|**P**|
|Cambiar a la herramienta Pincel|**B**|
|Cambiar a la herramienta Relleno|**F**|
|Cambiar a la herramienta Borrador|**E**|
|Cambiar a la herramienta Texto|**T**|
|Cambiar a la herramienta Selección de color (cuentagotas)|**I**|
|Mover la selección activa y su contenido|Teclas de **dirección**|
|Cambiar el tamaño de la selección activa y de su contenido|**Ctrl**+**Teclas de dirección**|
|Mover la selección activa, pero no su contenido|**Mayús**+**Teclas de dirección**|
|Cambiar el tamaño de la selección activa, pero no de su contenido|**Mayús**+**Ctrl**+**Teclas de dirección**|
|Confirmar la capa actual|**Return**|
|Disminuir el grosor de la herramienta|**[**|
|Aumentar el grosor de la herramienta|**]**|

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Trabajar con activos 3D para juegos y aplicaciones](../designers/working-with-3-d-assets-for-games-and-apps.md)|Proporciona información general sobre las herramientas que puede utilizar en Visual Studio para trabajar con recursos gráficos, como texturas e imágenes, modelos 3D y efectos de sombreador.|
|[Editor de modelos](../designers/model-editor.md)|Describe cómo usar el Editor de modelos de Visual Studio para trabajar con modelos 3D.|
|[Diseñador de sombras](../designers/shader-designer.md)|Describe cómo usar el diseñador de sombras de Visual Studio para trabajar con sombreadores.|