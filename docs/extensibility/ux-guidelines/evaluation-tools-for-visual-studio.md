---
title: Herramientas de evaluación de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a149d9163e61dd49105f123b373ecd9c7c1c278
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147338"
---
# <a name="evaluation-tools-for-visual-studio"></a>Herramientas de evaluación de Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista de comprobación de acabado de Visual Studio  
 Use esta lista de comprobación para evaluar la calidad de la experiencia de usuario para obtener más información visual y la interacción.  
  
### <a name="overview"></a>Información general  
  
-   Compruebe que todos los comandos dan como resultado de comentarios que indique a los usuarios que se han efectuado sus comandos.  
  
-   Compruebe que todos los elementos de interfaz de usuario y los controles son visibles en todos los temas y en modo de contraste alto.  
  
-   Compruebe que siempre se diferencian selección inactiva y activa, tanto en modo de contraste alto y estándar.  
  
-   Compruebe que foco siempre está visible y aparente.  
  
### <a name="performance"></a>Rendimiento  
  
-   Compruebe que el indicador de algún tipo de "ocupado" aparece si un comando tiene más de un segundo que se complete.  
  
-   Compruebe que si un comando tarda más de 10 segundos en completarse, una barra de progreso explícita, o bien determinado (opción preferida) o indeterminado, se muestra.  
  
### <a name="ui-text"></a>Texto de la interfaz de usuario  
  
-   Compruebe que todas las etiquetas distinguen mayúsculas de la frase o el título y que no hay texto está completamente en minúsculas.  
  
    ||Corregir|Incorrecto|  
    |-|-------------|---------------|  
    |**Texto del comando (todos)**|Tipo de oración:<br /><br /> **Nombre del directorio:**|Nombre del directorio:|  
    |**Texto del botón (cliente)**|Título:<br /><br /> **[Establecer como predeterminada]**|VALOR PREDETERMINADO DE SET AS|  
    |**Texto del botón (con conexión)**|Tipo de oración:<br /><br /> **[Establecer como predeterminado]**||  
  
-   Compruebe que todas las etiquetas, excepto los encabezados de grupo y los botones, terminan con un signo de dos puntos y preceden el control con el que se complementa.  
  
-   Compruebe que botones, los comandos y los vínculos de comandos que inician la interfaz de usuario para capturar la entrada del usuario finalización en los puntos suspensivos **[...]** .  
  
     Ejemplos:  
  
    -   Un **[avanzadas...]**  botón en un cuadro de diálogo.  
  
    -   Las opciones de comando en el menú Herramientas (**Herramientas > opciones**) no se debe obtener un botón de puntos suspensivos, porque iniciar el cuadro de diálogo es la intención del comando.  
  
-   Compruebe que la interfaz de usuario no contiene ningún abreviaturas, excepto los términos estándar del sector. Por ejemplo, HTML ni TCP/IP necesario deletrear, aunque deben OOM (memoria insuficiente) y PII (información de identificación personal).  
  
### <a name="keyboard-access"></a>Acceso mediante el teclado  
  
-   Compruebe que hay una manera de realizar cada tarea con el teclado. Por lo general, esto se logra a través del acceso de teclado para cada control, pero para algunas áreas muy visuales, una solución como desplazándose hasta la vista de código es aceptable.  
  
-   Compruebe que puede cambiar mediante tabulación a través de controles en un orden lógico (de izquierda a derecha y de arriba a abajo). Aunque esto es una práctica recomendada para la mayoría de los controles, no todos los controles requieren este enfoque. Por ejemplo, compruebe ese botón de radio son controles en un grupo con una sola tabulación.  
  
-   Compruebe que todos los controles tienen las etiquetas y que cada etiqueta tiene una tecla de acceso (excepciones incluyen algunos controles no etiquetado que podrían seguir en un control con la etiqueta en la ficha).  
  
-   Compruebe que no hay ningún conflicto de tecla de acceso.  
  
### <a name="fonts"></a>Fuentes  
  
-   Compruebe que todas las fuentes (fuente, tamaño, color) se usan de forma coherente y mantienen la jerarquía.  
  
-   Compruebe que todos los elementos de interfaz de usuario usan el servicio de fuente del entorno. (Consulte [fuentes y el formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Para comprobar si el servicio se está utilizando, vaya a **Herramientas > Opciones > fuentes y colores**. En la lista desplegable de configuración, elija la fuente del entorno y cambie el nombre de fuente a algo asimilar diferente (por ejemplo, Harrington o Comic Sans) y establezca el tamaño a 12 pto. A continuación, haga clic en Aceptar. Es posible que deba reiniciar el IDE, pero la mayoría de la interfaz de usuario cambiará inmediatamente. Las áreas que no refleje el cambio de fuente incluso en el reinicio no usa la fuente del entorno.  
  
-   Compruebe que las fuentes que se deriva del servicio (por ejemplo, texto en negrita o ampliación) conservan su tamaño y el formato en relación con el texto "normal" cuando se cambia el tamaño de fuente del entorno.  
  
-   Compruebe que no hay ningún error de recorte debido a las fuentes aumentadas. Las fuentes que se pierda probablemente son el resultado de los controles de alto fijo o contenedores de alto fijo.  
  
### <a name="dialogs"></a>Cuadros de diálogo  
  
-   Compruebe que el título del cuadro de diálogo es el mismo que el comando que se inició.  
  
-   Compruebe que todos los controles estándares son coherentes con el sistema operativo: color de fondo es estándar y no los controles deben tener un estilo de plantilla re especial que hace que se muestren diferentes de los controles estándar.  
  
-   Compruebe que los márgenes dentro del formulario deben ser de 12 píxeles y deben aparecer uniforme y coherente.  
  
-   Compruebe que los cuadros de diálogo aparecen centrados en el shell IDE o en la ventana que se generó.  
  
-   Cuando es útil, puede cambiar el tamaño los cuadros de diálogo. Para los cuadros de diálogo que se puede cambiar el tamaño, compruebe que al cambiar el tamaño, los controles adecuados deben cambiar el tamaño mientras que otras partes del cuadro de diálogo permanezcan constantes.  
  
-   Compruebe que los cuadros de diálogo de tamaño variable conservan cualquier tamaño ajustado por el usuario (tamaño, la ubicación, expansión de controles de cuadro de diálogo y así sucesivamente).  
  
-   Compruebe que no hay ningún icono en la barra de título.  
  
-   Compruebe que no hay ningún botones Minimizar y maximizar en la barra de título.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>Botones de operación de cuadro de diálogo (sólo cliente frente a)  
  
-   Compruebe que los botones de operación se encuentran en este orden: **Aceptar**, **cancelar**, **aplicar**.  
  
-   Compruebe que **Aceptar** y **cancelar** botones tienen el tamaño estándar: 23 x 75 píxeles.  
  
-   Compruebe que **Aceptar** y **cancelar** botones son del mismo tamaño, independientemente de la longitud de la cadena.  
  
-   Si la etiqueta de un botón de la operación requiere que el botón de más anchas que estándar, compruebe que el correspondiente **cancelar** botón es del mismo tamaño.  
  
-   Compruebe que hay un relleno de 6 píxeles entre los botones y los controles asociados.  
  
-   Compruebe que la **Aceptar** y **cancelar** botones no tienen teclas de acceso definida por una letra subrayada.  
  
-   Compruebe que un botón (normalmente **Aceptar**) tiene el foco de forma predeterminada.  
  
-   Compruebe que **Esc** cancela el cuadro de diálogo  
  
-   Compruebe que **ENTRAR** ejecuta el botón predeterminado si el foco no está en un control que procesa ENTRAR.  
  
-   Compruebe que la **Aceptar** y **cancelar** botones se colocan en la esquina inferior derecha del cuadro de diálogo. En raras excepciones, es aceptable para la que se apilan verticalmente en la esquina superior derecha.  
  
-   Compruebe que la configuración vertical se usa solo si otros botones que se encuentran en una alineación horizontal en el cuadro de diálogo.  
  
### <a name="control-standards"></a>Estándares de control  
  
#### <a name="general"></a>General  
  
-   Compruebe que, cuando sea posible, hay buenos valores predeterminados para acelerar la interacción del usuario y dirigir a los usuarios hacia un resultado seguro o comunes.  
  
-   Compruebe que los controles estándar comportan de la misma manera para que los usuarios sepan lo que ocurrirá según la experiencia anterior.  
  
#### <a name="label-controls"></a>Controles de etiqueta  
  
-   Compruebe que cada control tiene una etiqueta y que cada etiqueta visualmente se empareja con su control (generalmente dentro de un intervalo de píxel de 4 a 6) y es más cercano a su control correspondiente que para otros controles.  
  
-   Compruebe que las etiquetas se colocan vaciar izquierda con el control si situado por encima del borde izquierdo y centra horizontalmente, para que la línea de base de la etiqueta se alinea con la línea base del texto de entrada si situado a la izquierda.  
  
-   Compruebe que si se colocan varias etiqueta apilada y controles de entrada a la izquierda de un control, vaciar se mantienen las etiquetas y una distancia equivalente desde el borde del cuadro de diálogo, nunca vaciar derecha y una distancia equivalente de los controles. Pares deben distribuirse uniformemente a menos que necesita espacio adicional para indicar la agrupación.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controles de entrada (cuadros de texto y cuadros combinados)  
  
-   Compruebe que, cuando se utiliza la fuente del entorno de forma predeterminada, el alto de pantalla de cuadros de texto, cuadros combinados y botones son 23 todos los píxeles.  
  
-   Si se utiliza el texto de la sugerencia, compruebe que el color esté establecido en `Environment.ControlEditHintText` mediante el servicio de color.  
  
-   Si el campo es un campo obligatorio que se debe identificar como tal, compruebe:  
  
    -   que el fondo se establece en `Environment.ControlEditRequiredBackground` y primer plano se establece en `Environment.ControlEditRequiredHintText`  
  
    -   que hay texto de sugerencia en el control que aparece como **"\<necesario >"**  
  
#### <a name="button-controls"></a>Controles de botón  
  
-   Compruebe que los botones sean un tamaño mínimo de 75 x 23 píxeles, a menos que ajustando la longitud del texto.  
  
-   Compruebe que los botones han dejado y los márgenes de 3 a 5 píxeles, así como relleno para el contenido de la derecha.  
  
-   Es aceptable utilizar un cuadrado pequeño botón con sólo puntos suspensivos **[...]**  en ella en lugar de un **[Examinar...]**  botón (o una funcionalidad similar). Si usa, compruebe que el botón es 23 x 23 de tamaño.  
  
-   Si hay más de un **[Examinar...]**  botón en un cuadro de diálogo, a continuación, compruebe que la versión abreviada (solo puntos suspensivos **[...]** ) se utiliza para todas.  
  
-   Compruebe que puntos suspensivos **[...]**  botones no tiene una tecla de acceso. Cuando el foco está en el control de entrada junto a él, una pestaña debe mover el foco en el botón de puntos suspensivos.  
  
-   Compruebe que los botones, los comandos y los vínculos de comandos que inician la interfaz de usuario secundaria que captura más proporcionados por el usuario deben terminar en los puntos suspensivos **[...]** .  
  
#### <a name="hyperlinks"></a>Hipervínculos  
  
-   Compruebe que un control de hipervínculo nunca parpadea rojo cuando está activo. Se trata de un indicador de que el servicio de color no se va a usar  
  
-   Compruebe que los colores de VS utilizados son:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Compruebe que los hipervínculos aparecen azules con ningún subrayado, a menos que se incrustan en un párrafo.  
  
#### <a name="check-boxes"></a>Casillas de verificación  
  
-   Si una casilla de verificación tiene texto de varias líneas, compruebe que el cuadro se alinee con la primera línea de texto, no debe centrada verticalmente en todas las líneas.  
  
-   Compruebe que casillas de verificación siempre indica una opción binaria y no el usuario navegue por o abrir nuevas ventanas o páginas.  
  
-   Si una casilla de verificación presenta una opción relacionada con un control de entrada, comprobar que está colocado vaciar izquierdo y cierre muy bajo ese control para indicar a su relación.  
  
-   Compruebe que es una casilla de verificación **nunca** usa como un medio para habilitar todo el contenido de un cuadro de diálogo o una página.  
  
#### <a name="group-boxes"></a>Cuadros de grupo  
  
-   Compruebe que un cuadro de diálogo no contiene un cuadro de grupo único dentro de él que contiene todo el contenido del cuadro de diálogo.  
  
-   Compruebe que hay al menos dos controles dentro de cada cuadro de grupo.  
  
-   Rara vez se debe haber más de dos cuadros de grupo en un cuadro de diálogo.  
  
-   Compruebe que no hay ningún cuadro de grupo anidado.  
  
### <a name="icons"></a>Iconos  
  
-   Compruebe que los iconos aparecen invertidos correctamente cuando se encuentra en el tema oscuro.  
  
-   Compruebe que todos los iconos se basan en conceptos básicos.  
  
-   Compruebe que cada icono es distinto, fácil de reconocer y no contiene más de dos conceptos (sin el modificador de estado/language).  
  
-   Compruebe que el icono base aparece centrado en el espacio.  
  
-   Compruebe que todos los iconos aparecen legibles en el modo de contraste alto.  
  
-   Compruebe que cualquier color que se usa se alinee con las normas de uso de color.  
  
-   Compruebe que no hay ningún halos (bordes) alrededor de iconos. (Si está presente, el halo debe coincidir con el color de fondo de la interfaz de usuario adyacente).  
  
### <a name="touch-enabled-ui"></a>Interfaz de usuario táctil  
  
-   Compruebe que los controles interactivos son lo suficientemente grandes como para ser fácilmente touchable: mínimo **23 x 23 píxeles** de tamaño  
  
-   Compruebe que los controles usados con más frecuencia son al menos **40 por 40 píxeles** de tamaño.  
  
-   Compruebe que los controles interactivos tienen al menos **5 píxeles de espaciado** entre ellos