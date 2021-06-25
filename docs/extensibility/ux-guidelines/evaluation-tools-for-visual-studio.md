---
title: Herramientas de evaluación para Visual Studio | Microsoft Docs
description: Use esta lista de comprobación para evaluar la calidad de la experiencia del usuario para los detalles visuales y de interacción de las nuevas características que diseñe para Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baee9f3e2eaefcd659f8428bd566711949d0fe90
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900764"
---
# <a name="evaluation-tools-for-visual-studio"></a>Herramientas de evaluación para Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista de comprobación de la Visual Studio
 Use esta lista de comprobación para evaluar la calidad de la experiencia del usuario para obtener detalles visuales y de interacción.

### <a name="overview"></a>Información general

- Compruebe que todos los comandos tienen como resultado comentarios que indiquen a los usuarios que sus comandos se han realizado.

- Compruebe que todos los controles y elementos de la interfaz de usuario están visibles en todos los temas y contraste alto modo.

- Compruebe que la selección inactiva y activa siempre se diferencian, tanto en modo estándar como contraste alto activo.

- Compruebe que el foco siempre es visible y evidente.

### <a name="performance"></a>Rendimiento

- Compruebe que se muestra algún tipo de indicador "ocupado" si un comando tarda más de un segundo en completarse.

- Compruebe que si un comando tarda más de 10 segundos en completarse, se muestra una barra de progreso explícita, determinada (preferida) o indeterminada.

### <a name="ui-text"></a>Texto de la interfaz de usuario

- Compruebe que todas las etiquetas son oraciones o mayúsculas y minúsculas y que ningún texto está completamente en minúsculas.

    ||Correcto|Incorrecto|
    |-|-------------|---------------|
    |**Texto del comando (todos)**|Caso de oración:<br /><br /> **Nombre del directorio:**|Nombre del directorio:|
    |**Texto del botón (cliente)**|Mayúsculas y minúsculas:<br /><br /> **[ Establecer como valor predeterminado ]**|ESTABLECER COMO VALOR PREDETERMINADO|
    |**Texto del botón (en línea)**|Caso de oración:<br /><br /> **[ Establecer como valor predeterminado ]**||

- Compruebe que todas las etiquetas, excepto los encabezados de grupo y los botones, terminan con dos puntos y preceden al control con el que están emparejadas.

- Compruebe que los botones, comandos y vínculos de comandos que inician la interfaz de usuario para capturar la entrada del usuario terminan en un botón de puntos suspensivos **[...]**.

  Ejemplos:

  - Botón **[Avanzado...]** en un cuadro de diálogo.

  - Las opciones de comando del menú Herramientas **(Herramientas > Opciones**) no deben obtener puntos suspensivos, ya que iniciar el propio cuadro de diálogo es la intención del comando.

- Compruebe que la interfaz de usuario no contiene abreviaturas, excepto los términos estándar del sector. Por ejemplo, no es necesario escribir html ni TCP/IP, aunque deben ser OOM (memoria fuera de memoria) y PII (información de identificación personal).

### <a name="keyboard-access"></a>Acceso mediante el teclado

- Compruebe que hay una manera de realizar cada tarea con el teclado. Por lo general, esto se logra a través del acceso mediante teclado para cada control, pero para algunas áreas muy visuales, una solución alternativa como ir a la vista de código es aceptable.

- Compruebe que puede usar controles con tabulación en un orden lógico (de izquierda a derecha y de arriba a abajo). Aunque se trata de un procedimiento recomendado para la mayoría de los controles, no todos los controles requieren este enfoque. Por ejemplo, compruebe que los controles de botón de radio están en un grupo con una sola tabulación.

- Compruebe que todos los controles tienen etiquetas y que cada etiqueta tiene una mnemotécnica (las excepciones incluyen algunos controles no etiquetados que podrían seguir a un control etiquetado en la pestaña).

- Compruebe que no hay conflictos mnemotécnicos.

### <a name="fonts"></a>Fuentes

- Compruebe que todas las fuentes (cara, tamaño, color) se usan de forma coherente y mantienen la jerarquía.

- Compruebe que todos los elementos de la interfaz de usuario usan el servicio de fuentes del entorno. (Vea [Fuentes y formato para obtener Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Para comprobar si se está utilizando el servicio, vaya **a Herramientas > opciones > fuentes y colores**. En la lista desplegable Configuración, elija Fuente de entorno y cambie la cara de fuente por algo estilísticamente diferente (por ejemplo, H pta o No sans) y establezca el tamaño en 12 puntos. A continuación, haga clic en Aceptar. Es posible que tenga que reiniciar el IDE, pero la mayoría de la interfaz de usuario cambiará inmediatamente. Las áreas que no recogen el cambio de fuente incluso al reiniciar no usan la fuente del entorno.

- Compruebe que las fuentes derivadas del servicio (por ejemplo, texto en negrita o ampliado) conservan su tamaño y formato en relación con el texto "normal" cuando se cambia el tamaño de fuente del entorno.

- Compruebe que no hay errores de recorte debido a fuentes ampliadas. Las fuentes que se recortan probablemente son el resultado de controles de alto fijo o contenedores de altura fija.

### <a name="dialogs"></a>Cuadros de diálogo

- Compruebe que el título del cuadro de diálogo es el mismo que el comando que lo inició.

- Compruebe que todos los controles estándar son coherentes con el sistema operativo: el color de fondo es estándar y ningún control debe tener un estilo especial con plantilla que los haga parecer diferentes de los controles estándar.

- Compruebe que los márgenes dentro del formulario deben ser de 12 píxeles y deben ser uniformes y coherentes.

- Compruebe que los cuadros de diálogo aparecen centrados en el shell del IDE o en la ventana que los generó.

- Cuando resulta útil, los diálogos deben poder cambiar de tamaño. Para los diálogos que se pueden cambiar de tamaño, compruebe que, al cambiar el tamaño, los controles adecuados deben cambiar de tamaño mientras otras partes del diálogo permanecen constantes.

- Compruebe que los diálogos que se pueden cambiar de tamaño conservan cualquier tamaño ajustado por el usuario (tamaño, ubicación, expansión de controles de diálogo, entre otros).

- Compruebe que no hay ningún icono en la barra de título.

- Compruebe que no hay botones Minimizar y Maximizar en la barra de título.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Botones de operación de diálogo (solo vs client)

- Compruebe que los botones de operación están en este orden: **Ok**, **Cancel**, **Apply**.

- Compruebe que **los botones Aceptar** **y** Cancelar tienen el tamaño estándar: 75 x 23 píxeles.

- Compruebe que **los botones Aceptar** **y** Cancelar tienen el mismo tamaño, independientemente de la longitud de la cadena.

- Si la etiqueta de un botón de operación requiere que el botón sea más ancho que el estándar, compruebe que el botón **Cancelar** correspondiente tiene el mismo tamaño.

- Compruebe que hay un relleno de 6 píxeles entre los botones y los controles asociados.

- Compruebe que los  **botones Aceptar** y Cancelar no tienen teclas mnemotécnicas (claves de acceso definidas por una letra subrayada).

- Compruebe que un botón (normalmente **correcto)** tiene el foco de forma predeterminada.

- Comprobar que **Esc** cancela el cuadro de diálogo

- Compruebe que **Entrar** ejecuta el botón predeterminado si el foco no está en un control que procesa Entrar.

- Compruebe que los **botones Aceptar** **y** Cancelar están situados en la esquina inferior derecha del cuadro de diálogo. En raras excepciones, es aceptable que se apilen verticalmente en la esquina superior derecha.

- Compruebe que la configuración vertical solo se usa si otros botones están en una alineación horizontal dentro del cuadro de diálogo.

### <a name="control-standards"></a>Estándares de control

#### <a name="general"></a>General

- Compruebe que, cuando sea posible, hay buenos valores predeterminados para acelerar la interacción del usuario y dirigir a los usuarios hacia un resultado seguro o común.

- Compruebe que los controles estándar se comportan de la misma manera para que los usuarios sepan lo que ocurrirá en función de la experiencia anterior.

#### <a name="label-controls"></a>Controles de etiqueta

- Compruebe que cada control tiene una etiqueta y que cada etiqueta está emparejada visualmente con su control (generalmente dentro de un intervalo de 4 a 6 píxeles) y está más cerca de su control correspondiente que de otros controles.

- Compruebe que las etiquetas se coloquen vacías a la izquierda con el borde izquierdo del control si están posicionadas por encima y centradas horizontalmente, de modo que la línea base de la etiqueta se alinee con la línea base del texto de entrada si se coloca a la izquierda.

- Compruebe que si hay varios controles de entrada y etiqueta apilados situados a la izquierda de un control, las etiquetas se vacían a la izquierda y una distancia igual desde el borde del cuadro de diálogo, nunca se vacían a la derecha y a una distancia igual a la de los controles. Los pares se deben distribuir uniformemente a menos que necesiten espaciado adicional para indicar la agrupación.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controles de entrada (cuadros de texto y cuadros combinados)

- Compruebe que cuando se usa la fuente de entorno predeterminada, el alto de presentación de los cuadros de texto, los cuadros combinados y los botones son todos de 23 píxeles.

- Si se usa texto de sugerencia, compruebe que el color está establecido en `Environment.ControlEditHintText` mediante el servicio de color.

- Si el campo es un campo obligatorio que debe identificarse como tal, compruebe:

  - que el fondo está establecido en `Environment.ControlEditRequiredBackground` y el primer plano está establecido en `Environment.ControlEditRequiredHintText`

  - que hay texto de sugerencia dentro del control que aparece como **" \<Required> "**

#### <a name="button-controls"></a>Controles de botón

- Compruebe que los botones tienen un tamaño mínimo de 75 x 23 píxeles, a menos que se acomente texto más largo.

- Compruebe que los botones tienen márgenes izquierdo y derecho de 3 a 5 píxeles, así como relleno para el contenido.

- Es aceptable usar un botón cuadrado pequeño con solo puntos suspensivos **[...]** en lugar de un **botón [Examinar...]** (o una funcionalidad similar). Si se usa, compruebe que el botón tiene un tamaño de 23 x 23.

- Si hay más de un **botón [Examinar...]** en un cuadro de diálogo, compruebe que la versión abreviada **(solo** puntos suspensivos [...] ) se usa para todos.

- Compruebe que los botones de puntos **suspensivos [...]** no tienen una mnemotécnica. Cuando el foco está en el control de entrada situado junto a él, una pestaña debe mover el foco al botón de puntos suspensivos.

- Compruebe que los botones, comandos y vínculos de comandos que inician la interfaz de usuario secundaria que captura más entradas del usuario deben terminar en puntos suspensivos **[...]**.

#### <a name="hyperlinks"></a>Hipervínculos

- Compruebe que un control de hipervínculo nunca parpadea en rojo cuando está activo. Esto es un indicador de que el servicio de color no se está utilizando

- Compruebe que los colores de VS usados son:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Compruebe que los hipervínculos aparecen en azul sin subrayado, a menos que se inserten en un párrafo.

#### <a name="check-boxes"></a>Casillas

- Si una casilla tiene texto de varias líneas, compruebe que el cuadro se alinea con la primera línea de texto, no centrada verticalmente en todas las líneas.

- Compruebe que las casillas siempre indican una opción binaria y no navegan por el usuario ni abren nuevas ventanas o páginas.

- Si una casilla presenta una opción relacionada con un control de entrada, compruebe que está situado a la izquierda y muy cerca debajo de ese control para indicar su relación.

- Compruebe que nunca se usa una **casilla** como medio para habilitar todo el contenido de un cuadro de diálogo o página.

#### <a name="group-boxes"></a>Cuadros de grupo

- Compruebe que un cuadro de diálogo no contiene un único cuadro de grupo que contenga todo el contenido del diálogo.

- Compruebe que hay al menos dos controles dentro de cada cuadro de grupo.

- Rara vez debe haber más de dos cuadros de grupo en un cuadro de diálogo.

- Compruebe que no hay cuadros de grupo anidados.

### <a name="icons"></a>Iconos

- Compruebe que los iconos aparecen invertidos correctamente cuando están en el tema oscuro.

- Compruebe que todos los iconos se basan en conceptos básicos.

- Compruebe que cada icono es distinto, fácil de reconocer y no contiene más de dos conceptos (sin modificador de estado ni idioma).

- Compruebe que el icono base aparece centrado dentro del espacio.

- Compruebe que todos los iconos aparecen legibles contraste alto modo.

- Compruebe que cualquier color usado se alinea con los estándares de uso de colores.

- Compruebe que no hay halos (bordes) alrededor de los iconos. (Si está presente, el halo debe coincidir con el color de fondo de la interfaz de usuario adyacente).

### <a name="touch-enabled-ui"></a>Interfaz de usuario táctil

- Compruebe que los controles interactivos son lo suficientemente grandes como para que se puedan tocar fácilmente: un tamaño mínimo **de 23 x 23 píxeles.**

- Compruebe que los controles usados con más frecuencia tienen un tamaño de al menos **40 x 40 píxeles.**

- Compruebe que los controles interactivos tienen al **menos 5 píxeles de espaciado** entre ellos.
