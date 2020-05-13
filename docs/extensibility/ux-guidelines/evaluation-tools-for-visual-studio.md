---
title: Herramientas de evaluación para Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698427"
---
# <a name="evaluation-tools-for-visual-studio"></a>Herramientas de evaluación para Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista de verificación de artesanía para Visual Studio
 Utilice esta lista de comprobación para evaluar la calidad de la experiencia del usuario para obtener detalles visuales y de interacción.

### <a name="overview"></a>Información general

- Compruebe que todos los comandos dan como resultado comentarios que indican a los usuarios que sus comandos se han llevado a cabo.

- Compruebe que todos los elementos y controles de la interfaz de usuario están visibles en todos los temas y en el modo de contraste alto.

- Compruebe que la selección inactiva y activa siempre esté diferenciada, tanto en el modo estándar como en el modo de contraste alto.

- Compruebe que el enfoque siempre es visible y aparente.

### <a name="performance"></a>Rendimiento

- Verifique que se muestre algún tipo de indicador "ocupado" si un comando tarda más de un segundo en completarse.

- Compruebe que si un comando tarda más de 10 segundos en completarse, se muestra una barra de progreso explícita, ya sea determinada (preferida) o indeterminada.

### <a name="ui-text"></a>Texto de la interfaz de usuario

- Compruebe que todas las etiquetas son mayúsculas y minúsculas y que no hay texto en minúsculas.

    ||Correcto|Incorrecto|
    |-|-------------|---------------|
    |**Texto de comando (todos)**|Caso de sentencia:<br /><br /> **Nombre del directorio:**|Nombre del directorio:|
    |**Texto del botón (cliente)**|Caso de título:<br /><br /> **[ Establecer como predeterminado ]**|ESTABLECER COMO PREDETERMINADO|
    |**Texto del botón (en línea)**|Caso de sentencia:<br /><br /> **[ Establecer como predeterminado ]**||

- Compruebe que todas las etiquetas, excepto los encabezados y botones de grupo, terminan con dos puntos y preceden al control con el que están emparejados.

- Compruebe que los botones, comandos y vínculos de comandos que inician la interfaz de usuario para capturar la entrada del usuario terminan en puntos suspensivos **[...]**.

  Ejemplos:

  - Un botón **[Avanzado...]** en un cuadro de diálogo.

  - Las opciones de comando en el menú Herramientas (**Herramientas > Opciones**) no deben obtener puntos suspensivos, porque iniciar el propio cuadro de diálogo es la intención del comando.

- Compruebe que la interfaz de usuario no contiene abreviaturas, excepto los términos estándar del sector. Por ejemplo, ni HTML ni TCP/IP deben deletrearse, aunque OOM (fuera de memoria) y PII (información de identificación personal) deben ser deletreados.

### <a name="keyboard-access"></a>Acceso mediante el teclado

- Compruebe que hay una manera de realizar cada tarea con el teclado. Generalmente esto se logra a través del acceso al teclado para cada control, pero para algunas áreas altamente visuales, una solución alternativa como ir a la vista de código es aceptable.

- Compruebe que puede desplazarse por los controles en un orden lógico (de izquierda a derecha y de arriba a abajo). Aunque esta es una práctica recomendada para la mayoría de los controles, no todos los controles requieren este enfoque. Por ejemplo, compruebe que los controles de botón de opción están en un grupo con una sola tabulación.

- Compruebe que todos los controles tienen etiquetas y que cada etiqueta tiene un mnemotécnico (las excepciones incluyen algunos controles no etiquetados que podrían seguir un control etiquetado en la pestaña).

- Verifique que no haya conflictos mnemotécnicos.

### <a name="fonts"></a>Fuentes

- Compruebe que todas las fuentes (cara, tamaño, color) se utilizan de forma coherente y mantenga la jerarquía.

- Compruebe que todos los elementos de la interfaz de usuario utilizan el servicio de fuentes de entorno. (Consulte [Fuentes y formato para Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Para comprobar si se está utilizando el servicio, vaya a **Herramientas > Opciones > Fuentes y colores**. En el menú desplegable Configuración, elija Fuente de entorno y cambie la cara de fuente a algo estilísticamente diferente (como Harrington o Comic Sans) y establezca el tamaño en 12 pt. A continuación, haga clic en Aceptar. Es posible que deba reiniciar el IDE, pero la mayoría de la interfaz de usuario cambiará inmediatamente. Las áreas que no detectan el cambio de fuente incluso al reiniciar no utilizan la fuente de entorno.

- Compruebe que las fuentes derivadas del servicio (por ejemplo, texto en negrita o ampliado) conservan su tamaño y formato en relación con el texto "normal" cuando se cambia el tamaño de fuente del entorno.

- Compruebe que no hay errores de recorte debido a fuentes ampliadas. Las fuentes que se recortan son probablemente el resultado de controles de altura fija o contenedores de altura fija.

### <a name="dialogs"></a>Cuadros de diálogo

- Compruebe que el título del cuadro de diálogo es el mismo que el comando que lo inició.

- Compruebe que todos los controles estándar son coherentes con el sistema operativo: el color de fondo es estándar y que ningún control debe tener un estilo especial re-plantillado que los haga parecer diferentes de los controles estándar.

- Compruebe que los márgenes del formulario deben ser de 12 píxeles y deben aparecer uniformes y coherentes.

- Compruebe que los cuadros de diálogo aparecen centrados en el shell IDE o en la ventana que los generó.

- Cuando es útil, los cuadros de diálogo deben ser redimensionables. Para los cuadros de diálogo que son redimensionables, compruebe que al cambiar el tamaño, los controles adecuados deben cambiar el tamaño mientras que otras partes del cuadro de diálogo permanecen constantes.

- Compruebe que los cuadros de diálogo redimensionables conservan cualquier tamaño ajustado por el usuario (tamaño, ubicación, expansión de los controles de cuadro de diálogo, etc.).

- Compruebe que no hay ningún icono en la barra de título.

- Compruebe que no hay botones Minimizar y Maximizar en la barra de título.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Botones de operación de cuadro de diálogo (solo cliente VS)

- Compruebe que los botones de operación están en este orden: **Aceptar**, **Cancelar**, **Aplicar**.

- Compruebe que los botones **Aceptar** y **Cancelar** tienen el tamaño estándar: 75x23 píxeles.

- Compruebe que los botones **Aceptar** y **Cancelar** tienen el mismo tamaño, independientemente de la longitud de la cadena.

- Si la etiqueta de un botón de operación requiere que el botón sea más ancho que el estándar, compruebe que el botón **Cancelar** correspondiente es del mismo tamaño.

- Compruebe que hay un relleno de 6 píxeles entre los botones y los controles asociados.

- Compruebe que los botones **Aceptar** y **Cancelar** no tienen mnemotécnicas (claves de acceso definidas por una letra subrayada).

- Compruebe que un botón (normalmente **Aceptar**) tiene el foco de forma predeterminada.

- Compruebe que **Esc** cancela el cuadro de diálogo

- Compruebe que **Enter** ejecuta el botón predeterminado si el foco no está en un control que procesa Enter.

- Compruebe que los botones **Aceptar** y **Cancelar** están situados en la esquina inferior derecha del cuadro de diálogo. En raras excepciones, es aceptable que se apilen verticalmente en la parte superior derecha.

- Compruebe que la configuración vertical solo se utiliza si otros botones están en una alineación horizontal dentro del cuadro de diálogo.

### <a name="control-standards"></a>Normas de control

#### <a name="general"></a>General

- Compruebe que, cuando sea posible, hay buenos valores predeterminados para acelerar la interacción del usuario y dirigir a los usuarios hacia un resultado seguro o común.

- Compruebe que los controles estándar se comportan de la misma manera para que los usuarios sepan lo que sucederá en función de la experiencia anterior.

#### <a name="label-controls"></a>Controles de etiquetas

- Compruebe que cada control tiene una etiqueta y que cada etiqueta está emparejada visualmente con su control (generalmente dentro de un intervalo de 4-6 píxeles) y está más cerca de su control correspondiente que de otros controles.

- Compruebe que las etiquetas se colocan al ras a la izquierda con el borde izquierdo del control si se colocan encima y se centran horizontalmente, de modo que la línea base de la etiqueta se alinee con la línea base del texto de entrada si se coloca a la izquierda.

- Compruebe que si varios controles de entrada y etiqueta apilados se colocan a la izquierda de un control, las etiquetas se vacían a la izquierda y a la misma distancia del borde del cuadro de diálogo, nunca se vacían a la derecha y a la misma distancia de los controles. Los pares deben distribuirse uniformemente a menos que necesiten espaciado adicional para indicar la agrupación.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controles de entrada (cuadros de texto y cuadros combinados)

- Compruebe que, al utilizar la fuente de entorno predeterminada, la altura de visualización de los cuadros de texto, cuadros combinados y botones es de 23 píxeles.

- Si se utiliza texto de sugerencia, `Environment.ControlEditHintText` compruebe que el color está configurado para usar el servicio de color.

- Si el campo es un campo obligatorio que se debe identificar como tal, verifique:

  - que el fondo `Environment.ControlEditRequiredBackground` se establece en y el primer plano se establece en`Environment.ControlEditRequiredHintText`

  - que hay texto de sugerencia dentro del control que aparece como **\<"> requerido"**

#### <a name="button-controls"></a>Controles de botón

- Compruebe que los botones tienen un tamaño mínimo de 75x23 píxeles, a menos que se acomode texto más largo.

- Compruebe que los botones tienen márgenes izquierdo y derecho de 3-5 píxeles, así como relleno para el contenido.

- Es aceptable utilizar un pequeño botón cuadrado con sólo un punto suspensivo **[...]** en él en lugar de un botón **[Examinar...]** (o funcionalidad similar). Si se utiliza, compruebe que el botón tiene un tamaño de 23x23.

- Si hay más de un botón **[Examinar...]** en un cuadro de diálogo, compruebe que la versión abreviada (solo **ellipsis [...]**) se utiliza para todos.

- Compruebe que los botones de puntos suspensivos **[...]** no tienen un mnemotécnico. Cuando el foco está en el control de entrada junto a él, una pestaña debe mover el foco al botón de puntos suspensivos.

- Compruebe que los botones, comandos y vínculos de comandos que inician la interfaz de usuario secundaria que captura más entradas de usuario deben terminar en puntos suspensivos **[...]**.

#### <a name="hyperlinks"></a>Hipervínculos

- Compruebe que un control de hipervínculo nunca parpadea en rojo cuando está activo. Este es un indicador de que el servicio de color no se está utilizando

- Verifique que los colores VS usados sean:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Compruebe que los hipervínculos aparecen en azul sin subrayado a menos que estéincrustado en un párrafo.

#### <a name="check-boxes"></a>Casillas

- Si una casilla de verificación tiene texto de varias líneas, compruebe que la casilla se alinea con la primera línea de texto, no centrada verticalmente en todas las líneas.

- Compruebe que las casillas de verificación siempre indican una opción binaria y no navegue por el usuario ni abra nuevas ventanas o páginas.

- Si una casilla de verificación presenta una opción relacionada con un control de entrada, compruebe que se coloca al ras a la izquierda y muy cerca bajo ese control para indicar su relación.

- Compruebe que **nunca** se utilice una casilla de verificación como medio para habilitar todo el contenido de un cuadro de diálogo o página.

#### <a name="group-boxes"></a>Cajas de grupo

- Compruebe que un cuadro de diálogo no contiene un único cuadro de grupo que contenga todo el contenido del cuadro de diálogo.

- Compruebe que hay al menos dos controles dentro de cada cuadro de grupo.

- Rara vez debe haber más de dos cuadros de grupo en un cuadro de diálogo.

- Compruebe que no hay cuadros de grupo anidados.

### <a name="icons"></a>Iconos

- Compruebe que los iconos aparecen correctamente invertidos cuando está en el tema oscuro.

- Compruebe que todos los iconos se basan en conceptos básicos.

- Compruebe que cada icono es distinto, fácil de reconocer y no contiene más de dos conceptos (sin modificador de estado/idioma).

- Compruebe que el icono base aparece centrado en el espacio.

- Compruebe que todos los iconos aparecen legibles en el modo de contraste alto.

- Compruebe que cualquier color utilizado se alinee con los estándares de uso de color.

- Compruebe que no haya halos (bordes) alrededor de los iconos. (Si está presente, el halo debe coincidir con el color de fondo de la interfaz de usuario adyacente).

### <a name="touch-enabled-ui"></a>Interfaz de usuario táctil

- Compruebe que los controles interactivos son lo suficientemente grandes como para ser fácilmente táctiles - mínimo **23x23 píxeles** de tamaño

- Compruebe que los controles utilizados con más frecuencia tienen un tamaño mínimo de **40 x 40 píxeles.**

- Compruebe que los controles interactivos tengan al menos **5 píxeles de espaciado** entre ellos
