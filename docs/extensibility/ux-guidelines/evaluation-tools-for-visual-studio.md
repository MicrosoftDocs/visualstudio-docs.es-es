---
title: Herramientas de evaluación para Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00668fdebdbc8fc6a26c30a8762aa6f03d6e2769
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824566"
---
# <a name="evaluation-tools-for-visual-studio"></a>Herramientas de evaluación para Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista de comprobación de artesanía para Visual Studio
 Use esta lista de comprobación para evaluar la calidad de experiencia de usuario para obtener más información visual y la interacción.

### <a name="overview"></a>Información general

- Compruebe que todos los comandos dan como resultado los comentarios que se indica a los usuarios que se han efectuado sus comandos.

- Compruebe que todos los elementos de interfaz de usuario y los controles están visibles en todos los temas y en modo de contraste alto.

- Compruebe que siempre se diferencian selección inactiva y activa, tanto en modo de contraste alto y estándar.

- Compruebe que el foco siempre está visible y aparente.

### <a name="performance"></a>Rendimiento

- Compruebe que algún tipo de "ocupado" indicador se muestra si un comando tarda más de un segundo en completarse.

- Compruebe que si un comando tarda más de 10 segundos en completarse, una barra de progreso explícita, ya sea determinada (opción preferida) o indeterminado, se muestra.

### <a name="ui-text"></a>Texto de la interfaz de usuario

- Compruebe que todas las etiquetas son oración o en el título y que no hay texto está completamente en minúscula.

    ||Corregir|Incorrecto|
    |-|-------------|---------------|
    |**Texto del comando (todos)**|Oración:<br /><br /> **Nombre del directorio:**|Nombre del directorio:|
    |**Texto del botón (cliente)**|Título:<br /><br /> **[Establecer como predeterminada]**|VALOR PREDETERMINADO DE SET AS|
    |**Texto del botón (en línea)**|Oración:<br /><br /> **[Establecer como predeterminado]**||

- Compruebe que todas las etiquetas, excepto los encabezados de grupo y los botones, terminan con un signo de dos puntos y delante del control con el que estén emparejados.

- Compruebe que los botones, comandos y vínculos de comando que se inicie la interfaz de usuario para capturar la entrada del usuario finalización en los puntos suspensivos **[...]** .

  Ejemplos:

  - Un **[avanzadas...]**  botón en un cuadro de diálogo.

  - Las opciones de comando en el menú Herramientas (**Herramientas > opciones**) no se debe obtener un botón de puntos suspensivos porque iniciar el cuadro de diálogo es la intención del comando.

- Compruebe que la interfaz de usuario no contiene ningún abreviaturas, excepto los términos estándar del sector. Por ejemplo, HTML ni TCP/IP debe deletreado, aunque deben PII (información de identificación personal) y OOM (memoria insuficiente).

### <a name="keyboard-access"></a>Acceso mediante el teclado

- Compruebe que hay una manera de realizar cada tarea con el teclado. Por lo general, esto se logra a través del acceso de teclado para cada control, pero para algunas áreas altamente visuales, como la vista código alternativa es aceptable.

- Compruebe que puede desplazarse entre los controles en un orden lógico (de izquierda a derecha y de arriba a abajo). Aunque esto es una práctica recomendada para la mayoría de los controles, no todos los controles requieren este enfoque. Por ejemplo, comprobar ese botón de radio son controles en un grupo con una posición de tabulación único.

- Compruebe que todos los controles tienen las etiquetas y que cada etiqueta tiene una tecla de acceso (excepciones incluyen algunos controles sin etiquetar que podrían seguir en un control en la pestaña etiquetado).

- Compruebe que no hay ningún conflicto de tecla de acceso.

### <a name="fonts"></a>Fuentes

- Compruebe que todas las fuentes (face, size, color) se usan de forma coherente y mantienen la jerarquía.

- Compruebe que todos los elementos de interfaz de usuario usan el servicio de fuente del entorno. (Consulte [fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Para comprobar si se usa el servicio, vaya a **Herramientas > Opciones > fuentes y colores**. En la lista desplegable de configuración, elija la fuente del entorno y cambie el nombre de fuente a algo forma estilística diferente (por ejemplo, Harrington o el cómic SAN) y establezca el tamaño a 12 pt. A continuación, haga clic en Aceptar. Es posible que deba reiniciar el IDE, pero la mayoría de la interfaz de usuario cambiará inmediatamente. Las áreas que no recopilan el cambio de fuente incluso en el reinicio no están utilizando la fuente del entorno.

- Compruebe que las fuentes que se deriva del servicio (por ejemplo, texto en negrita o ampliada) conserven su tamaño y el formato en relación con el texto "normal" cuando se cambia el tamaño de fuente del entorno.

- Compruebe que no hay ningún error de recorte debido a las fuentes ampliadas. Las fuentes que recortan probablemente son el resultado de los controles de altura fija o contenedores de alto fijo.

### <a name="dialogs"></a>Cuadros de diálogo

- Compruebe que el título del cuadro de diálogo es el mismo que el comando que se inició.

- Compruebe que todos los controles estándares sean coherentes con el sistema operativo: color de fondo es estándar y no hay controles deben tener un estilo de plantilla re especial que hace que sea un aspecto diferente de los controles estándares.

- Compruebe que los márgenes dentro del formulario deben ser 12 píxeles y deben aparecer coherente y uniforme.

- Compruebe que los cuadros de diálogo aparecen centrados dentro del shell del IDE o la ventana que se generó.

- Cuando es útil, cuadros de diálogo deben ser redimensionables. Para los cuadros de diálogo que se puede cambiar el tamaño, compruebe que al cambiar el tamaño, los controles adecuados deben cambiar de tamaño mientras que otras partes del cuadro de diálogo permanezcan constantes.

- Compruebe que los diálogos redimensionables conservan cualquier tamaño ajustado por el usuario (tamaño, ubicación, expansión de los controles de cuadro de diálogo y así sucesivamente).

- Compruebe que no hay ningún icono en la barra de título.

- Compruebe que no hay ningún botón de minimizar y maximizar en la barra de título.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Botones de cuadro de diálogo (sólo cliente frente a)

- Compruebe que los botones de operación están en este orden: **Aceptar**, **cancelar**, **aplicar**.

- Compruebe que **Aceptar** y **cancelar** botones tienen el tamaño estándar: 75 x 23 píxeles.

- Compruebe que **Aceptar** y **cancelar** botones son del mismo tamaño, independientemente de la longitud de cadena.

- Si la etiqueta de un botón de la operación requiere el botón sea más ancha que estándar, compruebe que el correspondiente **cancelar** botón es del mismo tamaño.

- Compruebe que hay un relleno de 6 píxeles entre los botones y los controles asociados.

- Compruebe que la **Aceptar** y **cancelar** botones no tienen teclas de acceso definida por una letra subrayada.

- Compruebe que un botón (normalmente **Aceptar**) tiene el foco de forma predeterminada.

- Compruebe que **Esc** cancela el cuadro de diálogo

- Compruebe que **ENTRAR** el botón predeterminado se ejecuta si el foco no está en un control que procesa ENTRAR.

- Compruebe que la **Aceptar** y **cancelar** botones se colocan en la esquina inferior derecha del cuadro de diálogo. En raras excepciones, es aceptable para el que se apilan verticalmente en la esquina superior derecha.

- Compruebe que la configuración vertical se usa sólo si otros botones que se encuentran en una alineación horizontal en el cuadro de diálogo.

### <a name="control-standards"></a>Estándares de control

#### <a name="general"></a>General

- Compruebe que, cuando sea posible, hay valores por defecto buenos para acelerar la interacción del usuario y dirigir a los usuarios hacia un resultado común o seguro.

- Compruebe que los controles estándar comportan de la misma manera para que los usuarios sepan lo que ocurrirá según la experiencia anterior.

#### <a name="label-controls"></a>Controles de etiqueta

- Compruebe que cada control tiene una etiqueta y que cada etiqueta visualmente se empareja con su control (generalmente dentro de un intervalo de píxel 4-6) y está más cerca de su control correspondiente que a otros controles.

- Compruebe que las etiquetas se colocan vaciado izquierda con el control si coloca por encima del borde izquierdo y se centra horizontalmente, para que la línea de base de la etiqueta se alinea con la línea base del texto de entrada si se coloca a la izquierda.

- Compruebe que si se colocan varias apilada etiqueta y controles de entrada a la izquierda de un control, vaciado se dejan las etiquetas y una distancia equivalente desde el borde del cuadro de diálogo, no vaciar nunca derecha y una distancia equivalente de los controles. Los pares se deberían distribuir equitativamente a menos que necesita espacio adicional para indicar la agrupación.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controles de entrada (cuadros de texto y cuadros combinados)

- Compruebe que al usar la fuente del entorno de forma predeterminada, el alto de pantalla de los cuadros de texto, cuadros combinados y botones son todos 23 píxeles.

- Si se utiliza el texto de sugerencia, compruebe que el color esté establecido en `Environment.ControlEditHintText` mediante el servicio de color.

- Si el campo es un campo obligatorio que debe identificarse como tal, compruebe:

  - el fondo establecido en `Environment.ControlEditRequiredBackground` y primer plano se establece en `Environment.ControlEditRequiredHintText`

  - que hay dentro del control que aparece como texto de la sugerencia **"\<necesario >"**

#### <a name="button-controls"></a>Controles de botón

- Compruebe que los botones tienen un tamaño mínimo de 75 x 23 píxeles, a menos que se satisfaga la longitud del texto.

- Compruebe que los botones han derecho e izquierdo de los márgenes de 3 a 5 píxeles, así como relleno para el contenido.

- Es aceptable usar un botón cuadrado pequeño con solo puntos suspensivos **[...]**  en ella en lugar de un **[Examinar...]**  botón (o una funcionalidad similar). Si usa, compruebe que el botón es 23 x 23 de tamaño.

- Si hay más de un **[Examinar...]**  situado en un cuadro de diálogo y, después, compruebe que la versión abreviada (solo puntos suspensivos **[...]** ) se utiliza para todos.

- Comprobar que puntos suspensivos **[...]**  botones no tienen una tecla de acceso. Cuando el foco está en el control de entrada está junto a ella, una pestaña debe mover el foco al botón de puntos suspensivos.

- Compruebe que los botones, comandos y vínculos de comando que se inicie la interfaz de usuario secundaria que captura la entrada de usuario más deben terminar en los puntos suspensivos **[...]** .

#### <a name="hyperlinks"></a>Hipervínculos

- Compruebe que un control de hipervínculo nunca parpadea en color rojo cuando está activo. Esto es un indicador de que el servicio de color no se va a usar

- Compruebe que los colores VS utilizados son:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Compruebe que los hipervínculos aparecen azules con ningún carácter de subrayado, a menos que se incrusta en un párrafo.

#### <a name="check-boxes"></a>Casillas de verificación

- Si una casilla de verificación tiene texto de varias líneas, compruebe que la casilla se alinea con la primera línea de texto, que no se centra verticalmente en todas las líneas.

- Compruebe que las casillas de verificación siempre indican una elección binaria y no navegar por el usuario o abrir nuevas ventanas o páginas.

- Si una casilla de verificación presenta una opción relacionada con un control de entrada, comprobar que está colocado vaciado izquierda y muy cerca en ese control para indicar a su relación.

- Compruebe que es una casilla de verificación **nunca** usa como un medio para habilitar todo el contenido de un cuadro de diálogo o una página.

#### <a name="group-boxes"></a>Cuadros de grupo

- Compruebe que un cuadro de diálogo no contiene un cuadro de grupo único dentro de él que contiene todo el contenido del cuadro de diálogo.

- Compruebe que hay al menos dos controles dentro de cada cuadro de grupo.

- Casi nunca debería haber más de dos cuadros de grupo en un cuadro de diálogo.

- Compruebe que no hay ningún cuadro de grupo anidado.

### <a name="icons"></a>Iconos

- Compruebe que los iconos aparecen invertidos correctamente cuando se encuentra en el tema oscuro.

- Compruebe que todos los iconos se basan en los conceptos básicos.

- Compruebe que cada icono es distinto, fácil de reconocer y no tiene más de dos conceptos (sin el modificador/lenguaje de estado).

- Compruebe que el icono base aparece centrado en el espacio.

- Compruebe que todos los iconos aparecen legibles en el modo de contraste alto.

- Compruebe que cualquier color que se usa se alinea con los estándares de uso de color.

- Compruebe que no hay ningún halos (bordes) alrededor de los iconos. (Si está presente, el halo debe coincidir con el color de fondo de la interfaz de usuario adyacente).

### <a name="touch-enabled-ui"></a>Interfaz de usuario táctil

- Compruebe que los controles interactivos son lo suficientemente grandes como para ser fácilmente touchable: mínimo **23 x 23 píxeles** de tamaño

- Compruebe que los controles más usados son menos **40 x 40 píxeles** de tamaño.

- Compruebe que los controles interactivos tienen al menos **5 píxeles de espaciado** entre ellos
