---
title: Herramientas de evaluación para Visual Studio | Microsoft Docs
description: Use esta lista de comprobación para evaluar la calidad de la experiencia del usuario para ver los detalles visuales y de interacción de las nuevas características que diseña para Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6f23521763e73ef65b9c5a2f17acb54b85b71d63
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089893"
---
# <a name="evaluation-tools-for-visual-studio"></a>Herramientas de evaluación para Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista de comprobación de artesano para Visual Studio
 Use esta lista de comprobación para evaluar la calidad de la experiencia del usuario para los detalles visuales y de interacción.

### <a name="overview"></a>Información general

- Compruebe que todos los comandos dan como resultado comentarios que indican a los usuarios que se han llevado a cabo sus comandos.

- Compruebe que todos los elementos y controles de la interfaz de usuario están visibles en todos los temas y en modo contraste alto.

- Compruebe que la selección inactiva y activa siempre se diferencian en modo estándar y contraste alto.

- Compruebe que el foco está siempre visible y aparente.

### <a name="performance"></a>Rendimiento

- Compruebe que se muestra algún tipo de indicador "ocupado" Si un comando tarda más de un segundo en completarse.

- Compruebe que si un comando tarda más de 10 segundos en completarse, se muestra una barra de progreso explícita, ya sea Determinate (preferido) o indeterminada.

### <a name="ui-text"></a>Texto de la interfaz de usuario

- Compruebe que todas las etiquetas están en mayúsculas o minúsculas y que ningún texto está completamente en minúsculas.

    ||Correcto|Incorrecto|
    |-|-------------|---------------|
    |**Texto del comando (todos)**|Caso de oración:<br /><br /> **Nombre del directorio:**|Nombre del directorio:|
    |**Texto del botón (cliente)**|Caso de título:<br /><br /> **[Establecer como predeterminado]**|ESTABLECER COMO PREDETERMINADO|
    |**Texto del botón (en línea)**|Caso de oración:<br /><br /> **[Establecer como predeterminado]**||

- Compruebe que todas las etiquetas, excepto los encabezados de grupo y los botones, terminan con un signo de dos puntos y preceden al control con el que se emparejan.

- Compruebe que los botones, comandos y vínculos de comando inician la interfaz de usuario para capturar el extremo de entrada del usuario en un botón de puntos suspensivos **[...]**.

  Ejemplos:

  - Un botón **[avanzado...]** en un cuadro de diálogo.

  - Las opciones de comando en el menú Herramientas (**herramientas > opciones**) no deben tener puntos suspensivos, porque el inicio del cuadro de diálogo es el objetivo del comando.

- Compruebe que la interfaz de usuario no contenga abreviaturas, salvo por los términos estándar del sector. Por ejemplo, no es necesario escribir HTML ni TCP/IP, a pesar de que OOM (memoria insuficiente) e PII (información de identificación personal) deben hacerlo.

### <a name="keyboard-access"></a>Acceso mediante el teclado

- Compruebe que existe una forma de realizar cada tarea con el teclado. Por lo general, esto se consigue a través del acceso mediante teclado para cada control, pero para algunas áreas muy visuales, una solución alternativa como ir a la vista de código es aceptable.

- Compruebe que puede desplazarse por los controles en un orden lógico (de izquierda a derecha y de arriba abajo). Aunque se trata de una práctica recomendada para la mayoría de los controles, no todos los controles requieren este enfoque. Por ejemplo, compruebe que los controles de botón de radio están en un grupo con una sola tabulación.

- Compruebe que todos los controles tienen etiquetas y que cada etiqueta tiene un mnemotécnico (las excepciones incluyen algunos controles no etiquetados que pueden seguir a un control etiquetado en la pestaña).

- Compruebe que no hay ningún conflicto de mnemotécnico.

### <a name="fonts"></a>Fuentes

- Compruebe que todas las fuentes (caras, tamaño y color) se usan de forma coherente y mantienen la jerarquía.

- Compruebe que todos los elementos de la interfaz de usuario usan el servicio de fuente del entorno. (Consulte [fuentes y formato para Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Para comprobar si se está usando el servicio, vaya a **herramientas > opciones > fuentes y colores**. En el menú desplegable configuración, elija fuente del entorno y cambie la fuente a algo que sea distinto (por ejemplo, Harrington o Comic San) y establezca el tamaño en 12 pt. A continuación, haga clic en Aceptar. Es posible que tenga que reiniciar el IDE, pero la mayoría de la interfaz de usuario cambiará inmediatamente. Las áreas que no recogen el cambio de fuente incluso al reiniciar no usan la fuente del entorno.

- Compruebe que las fuentes derivadas del servicio (por ejemplo, negrita o texto agrandado) conserven su tamaño y formato en relación con el texto "normal" cuando cambie el tamaño de la fuente del entorno.

- Compruebe que no haya errores de recorte debido a las fuentes ampliadas. Las fuentes que se recortan probablemente son el resultado de los controles de alto fijo o de los contenedores de alto fijo.

### <a name="dialogs"></a>Cuadros de diálogo

- Compruebe que el título del cuadro de diálogo es el mismo que el comando que lo inició.

- Compruebe que todos los controles estándar son coherentes con el sistema operativo: el color de fondo es estándar y ningún control debe tener un estilo replantilla especial que hace que parezca diferente de los controles estándar.

- Compruebe que los márgenes del formulario deben ser de 12 píxeles y deben ser uniformes y coherentes.

- Compruebe que los cuadros de diálogo aparecen centrados en el Shell del IDE o en la ventana que los generó.

- Cuando es útil, se debe cambiar el tamaño de los cuadros de diálogo. En los cuadros de diálogo que se pueden cambiar de tamaño, compruebe que, al cambiar el tamaño, los controles adecuados deben cambiar de tamaño mientras que otras partes del cuadro de diálogo permanecen constantes.

- Compruebe que los cuadros de diálogo de tamaño variable conservan cualquier tamaño ajustado por el usuario (tamaño, ubicación, expansión de controles de cuadro de diálogo, etc.).

- Compruebe que no hay ningún icono en la barra de título.

- Compruebe que no hay botones minimizar y maximizar en la barra de título.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Botones de operación de cuadro de diálogo (solo cliente de VS)

- Compruebe que los botones de operación están en este orden: **Aceptar**, **Cancelar**, **aplicar**.

- Compruebe que los botones **Aceptar** y **Cancelar** tienen el tamaño estándar: 75x23 píxeles.

- Compruebe que los botones **Aceptar** y **Cancelar** tienen el mismo tamaño, independientemente de la longitud de la cadena.

- Si la etiqueta de un botón de operación requiere que el botón sea más ancho que el estándar, compruebe que el botón **Cancelar** correspondiente tiene el mismo tamaño.

- Compruebe que hay un relleno de 6 píxeles entre los botones y los controles asociados.

- Compruebe que los botones **Aceptar** y **Cancelar** no tienen teclas de acceso (teclas de acceso definidas por una letra subrayada).

- Compruebe que un botón (normalmente **correcto**) tiene el foco de forma predeterminada.

- Comprobar que **ESC** cancela el cuadro de diálogo

- Compruebe que **entrar** ejecuta el botón predeterminado si el foco no está en un control que procesa entrar.

- Compruebe que los botones **Aceptar** y **Cancelar** están colocados en la esquina inferior derecha del cuadro de diálogo. En raras excepciones, es aceptable apilarlas verticalmente en la parte superior derecha.

- Compruebe que la configuración vertical se usa solo si otros botones están en una alineación horizontal dentro del cuadro de diálogo.

### <a name="control-standards"></a>Estándares de control

#### <a name="general"></a>General

- Compruebe que, cuando sea posible, existen buenos valores predeterminados para acelerar la interacción del usuario y dirigir a los usuarios hacia un resultado común o seguro.

- Compruebe que los controles estándar se comportan de la misma manera para que los usuarios sepan lo que ocurrirá en función de la experiencia anterior.

#### <a name="label-controls"></a>Controles de etiqueta

- Compruebe que cada control tiene una etiqueta y que cada etiqueta se empareja visualmente con su control (generalmente dentro de un intervalo de 4-6 píxeles) y está más cerca de su control correspondiente que a otros controles.

- Compruebe que las etiquetas se colocan en la parte izquierda con el borde izquierdo del control si están colocadas encima y centradas horizontalmente, de modo que la línea de base de la etiqueta esté alineada con la línea base del texto de entrada si se coloca a la izquierda.

- Compruebe que, si hay varios controles de entrada y etiqueta apilados situados a la izquierda de un control, las etiquetas se alinean a la izquierda y a la misma distancia desde el borde del cuadro de diálogo, nunca se vacían a la derecha y a la misma distancia desde los controles. Los pares deben distribuirse uniformemente a menos que necesiten un espaciado adicional para indicar la agrupación.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controles de entrada (cuadros de texto y cuadros combinados)

- Compruebe que al usar la fuente de entorno predeterminada, el alto de la pantalla de los cuadros de texto, cuadros combinados y botones sea de 23 píxeles.

- Si se usa el texto de sugerencia, compruebe que el color esté establecido en `Environment.ControlEditHintText` con el servicio de color.

- Si el campo es obligatorio y debe identificarse como tal, compruebe lo siguiente:

  - que el fondo está establecido en `Environment.ControlEditRequiredBackground` y el de primer plano en `Environment.ControlEditRequiredHintText`

  - que hay texto de sugerencia en el control que aparece como **" \<Required> "**

#### <a name="button-controls"></a>Controles de botón

- Compruebe que los botones son un tamaño mínimo de 75x23 píxeles, a menos que se encuentre texto más largo.

- Compruebe que los botones tienen los márgenes izquierdo y derecho de 3-5 píxeles, así como el relleno del contenido.

- Es aceptable usar un pequeño botón cuadrado solo con puntos suspensivos **[...]** en lugar de un botón **[examinar...]** (o una funcionalidad similar). Si se usa, compruebe que el botón tiene un tamaño de 23x23.

- Si hay más de un botón **[examinar...]** en un cuadro de diálogo, compruebe que la versión abreviada (solo puntos suspensivos **[...]**) se usa para todos los.

- Compruebe que los botones de puntos suspensivos **[...]** no tienen un mnemotécnico. Cuando el foco está en el control de entrada situado junto a él, una pestaña debe cambiar el foco al botón de puntos suspensivos.

- Compruebe que los botones, comandos y vínculos de comandos que inician la interfaz de usuario secundaria que captura más entradas de usuario deben terminar con puntos suspensivos **[...]**.

#### <a name="hyperlinks"></a>Hipervínculos

- Compruebe que un control de hipervínculo nunca parpadee rojo cuando está activo. Este es un indicador de que el servicio de color no se está usando

- Compruebe que los colores de VS utilizados son:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Compruebe que los hipervínculos aparecen en azul sin subrayado a menos que estén incrustados en un párrafo.

#### <a name="check-boxes"></a>Casillas

- Si una casilla tiene texto de varias líneas, compruebe que el cuadro se alinea con la primera línea de texto, no centrada verticalmente en todas las líneas.

- Compruebe que las casillas siempre indican una opción binaria y que no navega al usuario ni abre nuevas ventanas o páginas.

- Si una casilla presenta una opción relacionada con un control de entrada, compruebe que está posicionada hacia la izquierda y muy cerca bajo ese control para indicar su relación.

- Compruebe que **nunca** se utiliza una casilla como medio para habilitar todo el contenido de un cuadro de diálogo o página.

#### <a name="group-boxes"></a>Cuadros de grupo

- Compruebe que un cuadro de diálogo no contiene un solo cuadro de grupo que contiene todo el contenido del cuadro de diálogo.

- Compruebe que hay al menos dos controles dentro de cada cuadro de grupo.

- Rara vez debe haber más de dos cuadros de grupo en un cuadro de diálogo.

- Compruebe que no hay ningún cuadro de grupo anidado.

### <a name="icons"></a>Iconos

- Compruebe que los iconos aparecen invertidas correctamente en el tema oscuro.

- Compruebe que todos los iconos se basan en conceptos básicos.

- Compruebe que cada icono es distinto, fácil de reconocer y no contiene más de dos conceptos (sin modificador de estado/idioma).

- Compruebe que el icono base aparece centrado en el espacio.

- Compruebe que todos los iconos aparecen legibles en modo de contraste alto.

- Compruebe que los colores utilizados se alineen con los estándares de uso de color.

- Compruebe que no hay halos (bordes) alrededor de los iconos. (Si está presente, el halo debe coincidir con el color de fondo de la interfaz de usuario adyacente).

### <a name="touch-enabled-ui"></a>Interfaz de usuario habilitada para Touch

- Comprobar que los controles interactivos son lo suficientemente grandes como para que se puedan tocar con facilidad: mínimo **23x23 píxeles** de tamaño

- Compruebe que los controles que se usan con más frecuencia tienen un tamaño de **40 x 40 píxeles** como mínimo.

- Comprobar que los controles interactivos tienen al menos **5 píxeles de espaciado** entre ellos
