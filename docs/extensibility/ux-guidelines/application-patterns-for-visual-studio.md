---
title: "Patrones de aplicaciones de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Patrones de aplicaciones de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="a-namebkmkwindowinteractionsa-window-interactions"></a><a name="BKMK_WindowInteractions"></a> Interacciones de ventana  
  
### <a name="overview"></a>Información general  
 Los dos tipos de ventana principal que se usa en Visual Studio son editores de documentos y ventanas de herramientas. Raras, pero posible, es grandes cuadros de diálogo no modales. Aunque se trata de todo no modales en el shell, sus patrones son muy diferentes. Este tema explica la diferencia entre las ventanas de documentos, ventanas de herramientas y cuadros de diálogo no modales. Patrones de cuadro de diálogo modal se tratan en [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Comparación de patrones de uso de la ventana  
 **Las ventanas de documento** también casi siempre se muestran en el documento. Esto ofrece al editor el documento "fase center" para organizar las ventanas de herramienta complementaria.  
  
 Un **ventana de herramientas** suelen aparecer como una ventana independiente más pequeña, que puede ser visible, oculto u oculto automático: contraído en el borde del IDE. Sin embargo, a veces se presentan dentro del documento y, para ello, desactive el **ventana/acoplamiento** propiedad en la ventana. El resultado más realistas, pero también decisión de diseño común: cuando se intenta integrar en Visual Studio, debe decidir si la característica debe mostrar una ventana de herramientas o una ventana de documento.  
  
 **Los cuadros de diálogo no modales** no se recomienda en Visual Studio. En gran medida, que son: por definición: ventanas de herramientas flotantes y deben implementarse como tal. Los cuadros de diálogo no modales se permiten en casos donde el tamaño de una ventana de herramientas normal acoplada a un lado del shell podría ser demasiado limitado. También se permiten en los casos donde el usuario pueda mover el cuadro de diálogo a un monitor secundario.  
  
 Piense cuidadosamente sobre qué tipo de contenedor que necesita. Consideraciones de patrón de uso común para el diseño de la interfaz de Usuario están en la tabla siguiente.  
  
||Ventana de documento|Ventana de herramientas|Cuadro de diálogo no modal|  
|-|---------------------|-----------------|---------------------|  
|**Posición**|Siempre coloca bien dentro del documento y no acoplar alrededor de los bordes del IDE. Se puede "tirar" para que flote por separado desde el shell principal.|Generalmente acopladas mediante fichas alrededor de los bordes del IDE, pero puede ser personalizadas que flota y oculta automáticamente (desanclado) o acoplada bien dentro del documento.|Ventana flotante grande independiente desde el IDE.|  
|**Confirmar el modelo**|*Confirmación retardada*<br /><br /> Para guardar los datos en un documento, el usuario debe emitir el comando Archivo/Guardar, guardar como o guardar todo. Una ventana de documento tiene el concepto de los datos que contiene "desfasadas", a continuación, se compromete a uno de la operación de guardar comandos. Al cerrar una ventana de documento, todo el contenido se guarda en disco o perdido.|*Confirmación inmediata*<br /><br /> No hay ningún Guardar modelo. Ventanas de herramientas del inspector que ayudan a editar un archivo, el archivo debe estar abierto en el editor o diseñador activo, y el editor o diseñador pertenece al guardar.|*Confirmación demorada o inmediata*<br /><br /> A menudo, un gran cuadro de diálogo no modal requiere una acción para confirmar los cambios y permite una operación "Cancelar", que se reviertan los cambios realizados en la sesión de diálogo.  Esto diferencia un cuadro de diálogo no modal desde una ventana de herramientas en que las ventanas de herramientas siempre tienen un modelo de confirmación inmediato.|  
|**Visibilidad**|*Abrir o crear (archivo) y cerrar*<br /><br /> Abrir un documento de windows se realiza a través de abrir un documento existente o usar una plantilla para crear un nuevo documento. No hay ninguna "abrir \< editor específico>" comando.|*Ocultar y mostrar*<br /><br /> Ventanas de herramientas de instancia única se pueden ocultas o se muestra. Contenido y los Estados de la ventana de herramientas mantener si en la vista u oculto. Ventanas de herramientas de varias instancias pueden ser cerradas así como ocultadas. Cuando se cierra una ventana de herramientas de varias instancias, se descarta el contenido y el estado en la ventana de herramientas.|*Iniciar desde un comando*<br /><br /> Los cuadros de diálogo se inician desde un comando basado en tareas.|  
|**Instancias**|*Instancias múltiples*<br /><br /> Varios editores pueden estar abiertos al mismo tiempo y edición de archivos diferentes, aunque algunos editores también permiten el mismo archivo que esté abierto en más de un editor (mediante la **ventana > nueva ventana** comando).<br /><br /> Un único editor puede estar editando uno o varios archivos al mismo tiempo (Diseñador de proyectos).|*Instance único o múltiple*<br /><br /> Contenido cambia para reflejar el contexto (como en el Explorador de propiedades) o enfoque y contexto de inserción a otras ventanas (lista de tareas, el Explorador de soluciones).<br /><br /> Ventanas de herramientas de instancia única y varias instancias deben asociarse con la ventana de documento activo a menos que haya una razón de peso no a.|*Instancia única*|  
|**Ejemplos**|**Editores de texto**, como el editor de código<br /><br /> **Superficies de diseño**, como un diseñador de formularios o una superficie de modelado<br /><br /> **Controlar diseños similares a los cuadros de diálogo**, como el Diseñador de manifiestos|El **el Explorador de soluciones** proporciona una solución y los proyectos incluidos dentro de la solución<br /><br /> El **Server Explorer** proporciona una vista jerárquica de los servidores y conexiones de datos que el usuario elige abrir en la ventana. Abrir un objeto de la jerarquía de la base de datos, como una consulta, abre una ventana de documento y permite al usuario editar la consulta.<br /><br /> El **Examinador de propiedades** muestra las propiedades para el objeto seleccionado en una ventana de documento o en otra ventana de herramientas. Las propiedades se muestran en una vista de cuadrícula jerárquica o en los controles de tipo cuadro de diálogo complejos y permiten al usuario establecer los valores de esas propiedades.||  
  
##  <a name="a-namebkmktoolwindowsa-tool-windows"></a><a name="BKMK_ToolWindows"></a> Ventanas de herramientas  
  
### <a name="overview"></a>Información general  
 Ventanas de herramientas permiten el trabajo del usuario que tiene lugar en ventanas de documento. Se puede utilizar para mostrar una jerarquía que representa un objeto raíz fundamentales que proporciona Visual Studio y que puede manipular.  
  
 Al considerar una nueva ventana de herramientas en el IDE, autores deben:  
  
-   Utilizar ventanas de herramientas existente adecuado para la tarea y no crear otros nuevos con una funcionalidad similar. Nuevas ventanas de herramientas sólo deben crearse si ofrecen un "herramienta" significativamente diferente o funcionalidad que no se puede integrar en una ventana similar o convirtiendo una ventana existente en un centro de dinamización.  
  
-   Usar una barra de comandos estándar, si es necesario, en la parte superior de la ventana de herramientas.  
  
-   Ser coherente con los modelos ya presentes en otras ventanas de herramientas de exploración de teclado y la presentación del control.  
  
-   Ser coherente con la presentación del control en otras ventanas de herramientas.  
  
-   Ventanas de herramientas específica del documento deben ser automática visible cuando sea posible para que aparezcan solo cuando se activa el documento principal.  
  
-   Asegúrese de que su contenido de la ventana es navegable mediante el teclado (teclas de dirección de soporte técnico).  
  
#### <a name="tool-window-states"></a>Estados de la ventana de herramienta  
 Ventanas de herramientas de Visual Studio tienen estados diferentes, algunos de los cuales están activados en el usuario (por ejemplo, la característica Ocultar automáticamente). Otros Estados, como auto visible que permita las ventanas de herramienta que aparezcan en el contexto correcto y ocultar cuando no sea necesario. Hay cinco estados de la ventana de herramienta en total.  
  
-   **Acoplar o anclado** ventanas de herramientas se pueden adjuntar a cualquiera de los cuatro lados del área del documento. Aparece el icono de alfiler en la barra de título de la ventana de herramienta. La ventana de herramientas se puede acoplar horizontal o verticalmente a lo largo del borde de shell y otras ventanas de herramientas y también se pueden vincular a fichas.  
  
-   **Ocultar automáticamente** están liberadas ventanas de herramientas. La ventana puede deslizar fuera de la vista, dejando una pestaña (con el nombre de la ventana de herramientas y su icono) en el borde del área del documento. La ventana de herramientas se desliza cuando un usuario se desplaza sobre la ficha.  
  
-   **Visible Auto** ventanas de herramientas aparecen automáticamente al otro fragmento de la interfaz de Usuario, como el editor, se inicia o adquiere foco.  
  
-   **Flotante** ventanas de herramientas mantenga el mouse fuera del IDE. Esto es útil para las configuraciones de varios monitores.  
  
-   **Fichas** ventanas de herramientas se pueden acoplar dentro del documento también. Esto es útil para ventanas de herramientas grandes, como el Examinador de objetos, que necesitan más realistas de permite acoplar a los bordes del marco.  
  
 ![Estados de la ventana de herramientas en Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")  
  
 **Estados de la ventana de herramientas en Visual Studio**  
  
#### <a name="single-instance-and-multi-instance"></a>Instancia única y varias instancias  
 Ventanas de herramientas son una instancia o varias instancias. Algunas ventanas de herramientas de instancia única podrían ser asociados a la ventana de documento activo mientras no ventanas de herramientas de varias instancias. Ventanas de herramientas de varias instancias responden al comando ventana ventana nuevo mediante la creación de una nueva instancia de la ventana. La siguiente imagen ilustra una habilitar el comando nueva ventana cuando se activa una instancia de la ventana de la ventana de herramientas:  
  
 ![Habilitar comandos de ventana de herramientas de Visual Studio](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")  
  
 **Habilitar el comando 'Nueva ventana' cuando está activa una instancia de la ventana de la ventana de herramientas**  
  
 Ventanas de herramientas de instancia única se pueden ocultas o muestran, mientras que ventanas de herramientas de varias instancias pueden cerradas, así como ocultadas. Pueden acoplar todas las ventanas de herramientas vinculada por ficha, flotante o establecer como una ventana secundaria de interfaz de múltiples documentos (MDI) (similar a una ventana de documento). Todas las ventanas de herramienta deben responder a los comandos de administración de la ventana correspondiente en el menú Ventana:  
  
 ![Comandos de administración de la ventana de Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")  
  
 **Comandos de administración de la ventana en el menú Ventana de Visual Studio**  
  
#### <a name="document-specific-tool-windows"></a>Ventanas de herramientas específica del documento  
 Algunas ventanas de herramientas están diseñadas para cambiar en función de un determinado tipo de documento. Estas ventanas actualizarán continuamente para reflejar la funcionalidad aplicable a la ventana del documento activo en el IDE.  
  
 Ejemplos de ventanas de herramientas cuyo contenido cambia para reflejar el editor seleccionado son el cuadro de herramientas y el esquema del documento. Estas ventanas muestran una marca de agua cuando un editor tiene el foco que no ofrece el contexto de la ventana.  
  
#### <a name="navigable-list-tool-windows"></a>Ventanas de herramientas de lista navegable  
 Algunas ventanas de herramientas muestran una lista de elementos navegables, con que el usuario puede interactuar. En este tipo de ventana, siempre debería haber comentarios para el elemento actual en la lista, incluso si la ventana está inactiva. La lista debe responder a la **GoToNextLocation** y **GoToPrevLocation** comandos, cambie también el elemento seleccionado actualmente en la ventana  
  
 Ejemplos de ventanas de herramientas de lista navegable son el Explorador de soluciones y la ventana de resultados de la búsqueda.  
  
### <a name="tool-window-types"></a>Tipos de ventana de herramienta  
  
#### <a name="common-tool-windows-and-their-functions"></a>Ventanas de herramientas comunes y sus funciones  
  
|Tipo|Ventana de herramientas|Función|  
|----------|-----------------|--------------|  
|**Jerarquía**|Explorador de soluciones|Un árbol jerárquico que muestra una lista de los documentos contenidos en elementos de la solución, proyectos y archivos varios. La visualización de los elementos dentro de los proyectos se define mediante el paquete al que pertenece el tipo de proyecto (por ejemplo, los tipos de basada en referencias, basada en directorio o en modo mixto).|  
|**Jerarquía**|Vista de clases|Un árbol jerárquico de las clases y los distintos elementos del conjunto de trabajo de documentos, independientemente de los propios archivos.|  
|**Jerarquía**|Explorador de servidores|Un árbol jerárquico que muestra todas las conexiones de datos y servidores de la solución.|  
|**Jerarquía**|Esquema del documento|La estructura jerárquica del documento activo.|  
|**Cuadrícula**|Propiedades|Una cuadrícula que muestra una lista de propiedades para el objeto seleccionado, junto con los selectores de valor pueden editar dichas propiedades.|  
|**Cuadrícula**|Lista de tareas|Una cuadrícula que permite al usuario crear, editar o eliminar tareas y comentarios.|  
|**Contenido**|Ayuda|Una ventana que permite a los usuarios acceso a diversos métodos de obtención de Ayuda de "¿cómo lo hago?" vídeos de los foros de MSDN.|  
|**Contenido**|Ayuda dinámica|Una ventana de herramientas que muestra vínculos a temas aplicables a la selección actual de ayuda.|  
|**Contenido**|Examinador de objetos|Un conjunto de marcos de dos columnas con una lista de componentes de objetos jerárquico en el panel izquierdo y el objeto propiedades y métodos en la columna derecha.|  
|**Cuadro de diálogo**|Buscar, búsqueda avanzada|Un cuadro de diálogo que permite al usuario buscar o buscar y reemplazar en varios archivos dentro de la solución.|  
|**Otros problemas**|Cuadro de herramientas|La ventana de herramientas que se utiliza para almacenar los elementos que se van a quitar en superficies de diseño, que proporciona una fuente de arrastre coherente para todos los diseñadores.|  
|**Otros problemas**|Página de inicio|Portal del usuario en Visual Studio, con acceso a las fuentes de noticias para desarrolladores, Ayuda de Visual Studio y proyectos recientes. Los usuarios también pueden crear páginas principales personalizadas copiar el archivo StartPage.xaml desde el directorio de archivos de programa "Common7\IDE\StartPages\" Visual Studio a la carpeta StartPages en el directorio de documentos de Visual Studio y edición de XAML manualmente o ábralo en Visual Studio u otro código de editor.|  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Automático||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Inmediato||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Salida|La ventana de salida se puede usar siempre tiene eventos textuales o estado a declarar.|  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Memoria||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Puntos de interrupción||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|En ejecución||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Documentos||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Pila de llamadas||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Locals||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Inspecciones||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Desensamblado||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Registros||  
|**Depurador:** un grupo de windows específicos para tareas de depuración y supervisión de actividades|Subprocesos||  
  
##  <a name="a-namebkmkdocumenteditorconventionsa-document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Convenciones de editor de documentos  
  
### <a name="document-interactions"></a>Interacciones de documento  
 "Documento también" es el mayor espacio en el IDE y es donde el usuario generalmente ha centrado su atención para completar sus tareas, asistidas por las ventanas de herramientas adicionales. Editores de documentos representan las unidades fundamentales de trabajo que el usuario se abre y se guarda dentro de Visual Studio. Mantienen un sentido sólido de selección vinculada al explorador de soluciones o en otras ventanas de la jerarquía de active. El usuario debe ser capaz de seleccione una de las ventanas de la jerarquía y sabe que contiene el documento y su relación a la solución, el proyecto u otro objeto raíz proporcionado por un paquete de Visual Studio.  
  
 Edición de documentos, requiere una experiencia de usuario coherente. Para permitir al usuario centrarse en la tarea en cuestión en lugar de en la administración de ventanas y encontrar comandos, seleccione una estrategia de vista de documento que mejor se adapte a las tareas de usuario para la edición de ese tipo de documento.  
  
#### <a name="common-interactions-for-the-document-well"></a>Interacciones habituales para el documento bien  
  
-   Mantener un modelo de interacción consistente en común **nuevo archivo** y **Abrir archivo** experiencias.  
  
-   Actualizar la funcionalidad relacionada en los menús y ventanas relacionadas cuando se abre la ventana de documento.  
  
-   Comandos de menú adecuadamente están integrados en los menús comunes como **Editar**, **formato**, y **vista** menús. Si hay una cantidad considerable de comandos especializados, a continuación, un nuevo menú puede crearse que es visible sólo cuando el documento tiene el foco.  
  
-   Una barra de herramientas incrustada puede colocarse en la parte superior del editor. Esto es preferible tener una barra de herramientas independiente que aparece fuera del editor.  
  
-   Mantenga siempre una selección en el Explorador de soluciones o activo similar ventana jerarquía.  
  
-   Haga doble clic en un documento en el Explorador de soluciones debe realizar la misma acción que **abiertos**.  
  
-   Si más de un editor puede utilizarse en un tipo de documento, el usuario debería poder invalidar o restablecer la acción predeterminada de un tipo de documento determinado mediante la **Abrir con** el cuadro de diálogo, haga doble clic en el archivo y seleccione **Abrir con** en el menú contextual.  
  
-   No cree a un asistente en un documento bien.  
  
### <a name="user-expectations-for-specific-document-types"></a>Expectativas del usuario para los tipos de documento específico  
 Hay varios tipos básicos de editores de documento y cada uno tiene un conjunto de interacciones que sean coherentes con otros usuarios del mismo tipo.  
  
-   **Editor de texto:** editor de código, archivos de registro  
  
-   **Superficie de diseño:** WPF forms diseñador, formularios Windows forms  
  
-   **Editor de estilo de cuadro de diálogo:** Diseñador de manifiestos, propiedades del proyecto  
  
-   **Diseñador de modelos:** Diseñador de flujo de trabajo, codemap, diagrama de arquitectura, progresión  
  
 También hay varios tipos de editor no que también usar el documento. Mientras que no edición documentos en Sí, es necesario que siga interacciones estándar para ventanas de documento.  
  
-   **Informes:** IntelliTrace informe, Hyper-V, informe del generador de perfiles  
  
-   **Panel:** concentrador de diagnósticos  
  
#### <a name="text-based-editors"></a>Editores de texto  
  
-   El documento participa en el modelo de ficha de vista previa, lo que permite obtener una vista previa del documento sin necesidad de abrirlo.  
  
-   La estructura del documento se puede representar dentro de una ventana de herramientas complementarias, por ejemplo, un esquema de documento.  
  
-   IntelliSense (si procede) se comportará de forma coherente con otros editores de código.  
  
-   Elementos emergentes o asistencia UI siga estilos y patrones similares para la interfaz de Usuario similar existente, como CodeLens.  
  
-   Mensajes de estado del documento se presentarán en un control de barra de información en la parte superior del documento o en la barra de estado.  
  
-   El usuario debe poder personalizar la apariencia de las fuentes y colores mediante un **Herramientas > Opciones de** página, la página fuentes y colores compartida o una específica para el editor.  
  
#### <a name="design-surfaces"></a>Superficies de diseño  
  
-   Un diseñador vacío debe tener una marca de agua en la superficie que indica cómo empezar a trabajar.  
  
-   Cambiar de vista mecanismos siguen patrones existentes como haga doble clic para abrir un editor de código o pestañas en la ventana de documento que permite la interacción con dos paneles.  
  
-   Agregar elementos a la superficie de diseño debe hacerse a través del cuadro de herramientas, a menos que se requiere una ventana de herramientas muy específicos.  
  
-   Elementos en la superficie siguen un modelo coherente de selección.  
  
-   Barras de herramientas incrustadas contienen comandos únicamente, no es común de comandos específicos del documento como **Guardar**.  
  
#### <a name="dialog-style-editors"></a>Editores de estilo de cuadro de diálogo  
  
-   Control del diseño debe seguir las convenciones de diseño de cuadro de diálogo normal.  
  
-   Tabulaciones en el editor no deberían coincidir con la apariencia de las fichas de documentos, debe coincidir con uno de los dos estilos de ficha interiores permitidos.  
  
-   Los usuarios deben poder interactuar con los controles mediante el teclado. ya sea mediante la activación del editor y tabulación a través de controles o utilizando las teclas de acceso estándar.  
  
-   El diseñador debe utilizar common guardar el modelo. No guardar general o los botones de confirmación se deben colocar en la superficie, aunque otros botones que pueden ser apropiado.  
  
#### <a name="model-designers"></a>Diseñadores de modelos  
  
-   Un diseñador vacío debe tener una marca de agua en la superficie que indica cómo empezar a trabajar.  
  
-   Agregar elementos a la superficie de diseño debe hacerse a través del cuadro de herramientas.  
  
-   Elementos en la superficie siguen un modelo coherente de selección.  
  
-   Barras de herramientas incrustadas contienen comandos únicamente, no es común de comandos específicos del documento como **Guardar**.  
  
-   Una leyenda puede aparecer en la superficie, indicativa o una marca de agua.  
  
-   El usuario debe poder personalizar la apariencia de las fuentes y colores mediante un **Herramientas > Opciones de** página, la página fuentes y colores compartida o una específica para el editor.  
  
#### <a name="reports"></a>Informes  
  
-   Los informes son normalmente sólo información y no participan en el modelo de guardar. Sin embargo, pueden incluir interacción como vínculos a otra información relevante o secciones que expandir y contraer.  
  
-   En la superficie de la mayoría de los comandos debe ser hipervínculos, no los botones.  
  
-   Diseño debe incluir un encabezado y siga las instrucciones de diseño de informe estándar.  
  
#### <a name="dashboards"></a>Paneles  
  
-   Paneles no tienen un modelo de interacción a sí mismos, pero sirven como medio para ofrecer una variedad de otras herramientas.  
  
-   No participar en el modelo de guardar.  
  
-   Los usuarios deben poder interactuar con los controles mediante el teclado, el editor de la activación y tabulación de controles o mediante teclas de acceso estándar.  
  
##  <a name="a-namebkmkdialogsa-dialogs"></a><a name="BKMK_Dialogs"></a> Cuadros de diálogo  
  
### <a name="introduction"></a>Introducción  
 Cuadros de diálogo en Visual Studio deben admitir normalmente una unidad discreta de trabajo del usuario y, a continuación, se descarta.  
  
 Si ha determinado que necesita un cuadro de diálogo, tiene tres opciones, en orden de preferencia:  
  
1.  Integrar características en uno de los cuadros de diálogo compartidos en Visual Studio.  
  
2.  Crear su propio cuadro de diálogo con un patrón que se encuentra en un cuadro de diálogo similar existente.  
  
3.  Crear un nuevo cuadro de diálogo, interacción siguiente y directrices de diseño.  
  
 Este tema describe cómo elegir el modelo correcto del cuadro de diálogo flujos de trabajo de Visual Studio y las convenciones de diseño del cuadro de diálogo común.  
  
### <a name="themes"></a>Temas  
 Cuadros de diálogo en Visual Studio siguen uno de los dos estilos básicos:  
  
#### <a name="standard-unthemed"></a>Estándar (unthemed)  
 La mayoría de los cuadros de diálogo son los cuadros de diálogo de la utilidad estándar y debe ser unthemed. No no controles comunes de plantilla re o intente crear botones "modernas" estilizados o controles. Controles y la apariencia de chrome siga [directrices de la interacción de escritorio de Windows estándares para cuadros de diálogo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Aplicar un tema  
 Cuadros de diálogo de Especialidad "firma" pueden ser con temas. Cuadros de diálogo con temas tienen una apariencia diferente, que también tiene algunos patrones de interacción especial asociados con el estilo. Tema el cuadro de diálogo si cumple estos requisitos:  
  
-   El cuadro de diálogo es una experiencia común que se ven y se utilizará a menudo o muchos usuarios (por ejemplo, el **nuevo proyecto** cuadro de diálogo.  
  
-   El cuadro de diálogo contiene los elementos de la marca de producto destacado (por ejemplo, el **configuración de la cuenta** cuadro de diálogo).  
  
-   El cuadro de diálogo aparece como una parte integral de un flujo mayor que incluye otros cuadros de diálogo con temas (por ejemplo, el **Agregar servicio conectado** cuadro de diálogo).  
  
-   El cuadro de diálogo es una parte importante de una experiencia que desempeña un papel estratégico en promocionar o diferenciar una versión del producto.  
  
 Al crear un cuadro de diálogo con temas, use los colores de entorno adecuadas y siga los patrones de interacción y diseño correcto. (Consulte [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))  
  
### <a name="dialog-design"></a>Diseño del cuadro de diálogo  
 Los cuadros de diálogo bien diseñadas tienen los siguientes elementos en cuenta:  
  
-   La tarea de usuario que se admita  
  
-   El estilo de texto del cuadro de diálogo, el idioma y la terminología  
  
-   Opción de control y convenciones de la interfaz de Usuario  
  
-   Alineación de especificación y control de diseño Visual  
  
-   Acceso mediante el teclado  
  
#### <a name="content-organization"></a>Organización de contenido  
 Tenga en cuenta las diferencias entre estos tipos básicos de los cuadros de diálogo:  
  
-   [Los cuadros de diálogo simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentar los controles en una sola ventana modal. La presentación podría incluir variaciones de patrones de control complejo, incluyendo un selector de campo o una barra de iconos.  
  
-   [Capas de cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) se usa para hacer más de espacio en pantalla cuando una única parte de la interfaz de Usuario consta de varios grupos de controles. Agrupaciones del cuadro de diálogo son "niveles" mediante controles de fichas, controles de lista de navegación o botones para que el usuario puede elegir que la agrupación para ver en un momento dado.  
  
-   [Asistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) son útiles para dirigir al usuario a través de una secuencia lógica de pasos hacia la finalización de una tarea. Se ofrecen una serie de opciones en los paneles secuenciales, introducción a veces a diferentes flujos de trabajo ("ramas") dependen de una elección realizada en el panel anterior.  
  
####  <a name="a-namebkmksimpledialogsa-simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Cuadros de diálogo simples  
 Un sencillo cuadro de diálogo es una presentación de controles en una sola ventana modal. Esta presentación podría incluir variaciones de patrones de control complejo, como un selector de campo. Para cuadros de diálogo simples, siga el diseño general estándar, así como cualquier diseño específico necesarios para las agrupaciones de control complejo.  
  
 ![Cuadro de diálogo sencillo en Visual Studio](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")  
  
 **Crear clave de nombre seguro es un ejemplo de un sencillo cuadro de diálogo en Visual Studio.**  
  
####  <a name="a-namebkmklayereddialogsa-layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Cuadros de diálogo en capas  
 Los cuadros de diálogo con capas incluyen fichas, paneles y los árboles incrustados. Se utilizan para maximizar el espacio cuando hay varios grupos de controles que se ofrecen en una única parte de la interfaz de Usuario. Las agrupaciones se dividen en capas para que el usuario puede elegir que la agrupación para ver en cualquier momento.  
  
 En el caso más sencillo, el mecanismo para cambiar entre grupos es un control de ficha. Hay varias alternativas disponibles. Consulte dar prioridad a y diseño de cómo elegir el estilo más adecuado.  
  
 El **Herramientas > opciones** cuadro de diálogo es un ejemplo de un cuadro de diálogo con capas mediante un árbol incrustado:  
  
 ![Cuadro de diálogo con capas en Visual Studio](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")  
  
 **Herramientas > opciones es un ejemplo de un cuadro de diálogo con capas en Visual Studio.**  
  
####  <a name="a-namebkmkwizardsa-wizards"></a><a name="BKMK_Wizards"></a> Asistentes  
 Los asistentes son útiles para dirigir al usuario a través de una secuencia lógica de pasos en la realización de una tarea. Se ofrecen una serie de opciones en los paneles secuenciales y el usuario debe seguir a través de cada paso antes de proceder a la siguiente. Una vez que hay suficientes valores predeterminados de la **Finalizar** botón está habilitado.  
  
 Modales asistentes se utilizan para tareas que:  
  
-   Contienen la bifurcación, donde se ofrecen distintas rutas dependiendo de las opciones de usuario  
  
-   Contiene dependencias entre los pasos, donde los pasos subsiguientes dependen de entrada del usuario en los pasos anteriores  
  
-   Son bastante complejas que se debe usar la interfaz de Usuario para explicar las opciones y los posibles resultados de cada paso  
  
-   Son transaccionales, que requieren un conjunto de pasos para completarse en su totalidad antes de confirmados los cambios  
  
### <a name="common-conventions"></a>Convenciones comunes  
 Para lograr un diseño óptimo y funcionalidad de los cuadros de diálogo, siga estas convenciones de tamaño del cuadro de diálogo, posición, estándares, configuración de control y alineación, UI texto, barras de título, botones de control y las teclas de acceso.  
  
 Para obtener instrucciones específicas del diseño, vea [diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Tamaño  
 Los cuadros de diálogo deben ajustarse a una resolución mínima de pantalla de 1024 x 768 y tamaño del cuadro de diálogo inicial no debe superar los 900 x 700 píxeles. Los cuadros de diálogo que puede cambiar el tamaño, pero no es un requisito.  
  
 Hay dos recomendaciones para diálogos redimensionables:  
  
1.  Que está definido para el cuadro de diálogo que se optimizan para el conjunto de controles sin recorte y se ajusta para adaptarse al crecimiento de localización razonable un tamaño mínimo.  
  
2.  Que el tamaño de la escala del usuario se conserva entre sesiones. Por ejemplo, si el usuario ajusta un cuadro de diálogo a 150%, un inicio posterior del cuadro de diálogo se mostrará al 150%.  
  
#### <a name="position"></a>Posición  
 Los cuadros de diálogo deben aparecer centrados en el IDE en el primer inicio. Para los cuadros de diálogo invariable, no es necesario que conservar la última posición del cuadro de diálogo, por lo que aparecerán centrado en lanzamientos posteriores. Para cuadros de diálogo puede cambiar el tamaño, el tamaño se debe conservar en lanzamientos posteriores. En los cuadros de tamaño variable que son modales, de la posición no deban conservarse. Mostrarlos centrado en el IDE evita la posibilidad de que el cuadro de diálogo que aparecen en una posición imprevisible o inutilizable cuando ha cambiado la configuración de pantalla del usuario. Cuadros de diálogo no modales que pueden cambiar la posición, la posición del usuario debe mantenerse en lanzamientos posteriores, como el cuadro de diálogo se puede utilizar con frecuencia como una parte integral de un flujo de trabajo mayor.  
  
 Cuando los cuadros de diálogo deben generar otros cuadros de diálogo, debe actuar en cascada en el cuadro de diálogo superior a la derecha y hacia abajo del primario para que sea obvio para el usuario que ha desplazado a un nuevo lugar.  
  
#### <a name="modality"></a>Modalidad  
 Modal que significa que los usuarios son necesarios para completar o cancelar el cuadro de diálogo antes de continuar. Puesto que los cuadros de diálogo modales bloquean al usuario interactuar con otras partes del entorno, flujo de tareas de la característica debe usarlas como con moderación como sea posible. Cuando es necesaria una operación modal, Visual Studio tiene un número de cuadros de diálogo compartidos, en que puede integrar características. Si debe crear un nuevo cuadro de diálogo, siga el patrón de interacción de un cuadro de diálogo existente con una funcionalidad similar.  
  
 Cuando los usuarios deben realizar dos actividades a la vez, como **Buscar** y **reemplazar** al escribir nuevo código, el cuadro de diálogo debe ser no modal para que el usuario puede alternar fácilmente entre ellos. Generalmente, Visual Studio utiliza ventanas de herramientas para este tipo de compatibilidad con el editor de la tarea vinculada.  
  
#### <a name="control-configuration"></a>Configuración de control  
 Ser coherente con las configuraciones de control existentes que consiguen lo mismo en Visual Studio.  
  
#### <a name="title-bars"></a>Barras de título  
  
-   El texto de la barra de título debe reflejar el nombre del comando que se inició.  
  
-   Icono no debe usarse en barras de título del cuadro de diálogo. En casos donde el sistema requiere uno, utilice el logotipo de Visual Studio.  
  
-   Los cuadros de diálogo no deberían tener minimizar o maximizar botones.  
  
-   Botones de ayuda en la barra de título han quedado desusados. No se agregan a los cuadros de diálogo nuevo. Cuando existen, se debe iniciar un tema de ayuda es conceptualmente relevante para la tarea.  
  
 ![Especificaciones de la barra de título para Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")  
  
 **Especificaciones de la directriz de barras de título de los cuadros de diálogo de Visual Studio.**  
  
#### <a name="control-buttons"></a>Botones de control  
 En general, **Aceptar**/**Cancelar**/**Ayuda** botones deberían estar organizados horizontalmente en la esquina inferior derecha del cuadro de diálogo. Si un cuadro de diálogo tiene varios otros botones en la parte inferior del cuadro de diálogo que se producirían visual confusión con los botones de control, se permite la pila vertical alternativa.  
  
 ![Controlar las configuraciones de botón en Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")  
  
 **Configuraciones aceptables para los botones de control de los cuadros de diálogo de Visual Studio**  
  
 El cuadro de diálogo debe incluir un botón de control predeterminado. Para determinar el comando recomendado para usar como valor predeterminado, elija entre las opciones siguientes (que se muestran en orden de prioridad):  
  
-   Elija el comando más seguro y más seguro como valor predeterminado. Esto significa que el comando más probable evitar la pérdida de datos y evitar el acceso al sistema imprevistos.  
  
-   Si la seguridad y pérdida de datos no son factores, a continuación, elija el comando predeterminado según su comodidad. Incluyendo el comando como el valor predeterminado es más probable que mejorará el flujo de trabajo del usuario cuando el cuadro de diálogo admite tareas repetitivas o frecuentes.  
  
 Evite elegir una acción destructiva permanentemente para el comando predeterminado. Si hay un comando de ese tipo, elija un comando más seguro en su lugar como valor predeterminado.  
  
#### <a name="access-keys"></a>Teclas de acceso  
 No utilice las teclas de acceso para **Aceptar**/**Cancelar**/**Ayuda** botones. Estos botones se asignan a teclas de método abreviado de forma predeterminada:  
  
|Nombre del botón|Método abreviado de teclado|  
|-----------------|-----------------------|  
|Aceptar|Entrar|  
|Cancelar|Esc|  
|Ayuda|F1|  
  
#### <a name="imagery"></a>Imágenes  
 Utilizar imágenes con moderación en los cuadros de diálogo. No utilice iconos grandes en los cuadros de diálogo simplemente para usar un espacio. Usar imágenes sólo si son una parte importante de la transmisión del mensaje para el usuario, como iconos de advertencia o animaciones de estado.  
  
###  <a name="a-namebkmkprioritizingandlayeringa-prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Establecer prioridades y disposición en capas  
  
#### <a name="prioritizing-your-ui"></a>Dar prioridad a la interfaz de Usuario  
 Podría ser necesario poner ciertos elementos de interfaz de Usuario a la vanguardia y coloque el comportamiento más avanzado y en los cuadros de diálogo Opciones (incluidos los comandos oscuros). Incorpore la funcionalidad frecuente a la vanguardia crear espacio para él y hacerlo visible de forma predeterminada en la interfaz de Usuario con una etiqueta de texto cuando se muestra el cuadro de diálogo.  
  
#### <a name="layering-your-ui"></a>Capas de la interfaz de Usuario  
 Si ha determinado que es necesario un cuadro de diálogo, pero la funcionalidad relacionada que desee presentar al usuario va más allá de lo que puede mostrarse en un cuadro de diálogo simple, necesitará la interfaz de Usuario de la capa. Visual Studio utiliza los métodos de capas más comunes son las pestañas y vestíbulos o paneles. En algunos casos, las regiones que se pueden expandir y contraer podrían ser adecuadas. Interfaz de Usuario adaptable generalmente no se recomienda en Visual Studio.  
  
 Hay ventajas y desventajas de los distintos métodos de disposición en capas de interfaz de Usuario a través de controles de pestaña similar. Revise la lista siguiente para asegurarse de que elige una técnica de capas que se ajuste a su situación.  
  
##### <a name="tabbing"></a>Tabulación  
  
|Mecanismo de conmutación|Ventajas y el uso apropiado|Uso inadecuado y desventajas|  
|-------------------------|------------------------------------|-----------------------------------------|  
|Control Tab|Agrupar páginas del cuadro de diálogo de forma lógica en conjuntos relacionados<br /><br /> Útil para menos de cinco (o el número de etiquetas que caben en una fila en el cuadro de diálogo) páginas de controles relacionados en el cuadro de diálogo<br /><br /> Pestaña etiquetas deben ser cortas: una o dos palabras que se puedan identificar fácilmente el contenido<br /><br /> Un estilo de cuadro de diálogo común de sistema<br /><br /> Ejemplo: **Explorador de archivos > Propiedades de los elementos**|Hacer etiquetas descriptivas de corto puede ser difícil<br /><br /> Por lo general no escala más allá de cinco pestañas en un cuadro de diálogo<br /><br /> Inadecuado si tiene demasiados pestañas para una fila. usar una técnica alternativa de capas<br /><br /> No extensible|  
|Exploración de la barra lateral|Dispositivo de conmutación simple que puede alojar más categorías de fichas<br /><br /> Lista plana de categorías (sin jerarquía)<br /><br /> Extensible<br /><br /> Ejemplo: **Personalizar... > Agregar comando**|No es un buen uso del espacio horizontal si hay menos de tres grupos<br /><br /> Podrían ser tareas más adecuadas para una lista desplegable|  
|Tree (control)|Permite categorías ilimitados<br /><br /> Permite la agrupación o la jerarquía de categorías<br /><br /> Extensible<br /><br /> Ejemplo: **Herramientas > Opciones**|Jerarquías muy anidadas pueden provocar excesivos de desplazamiento horizontal<br /><br /> Visual Studio tiene una gran abundancia de vistas de árbol|  
|Asistente|Ayuda en la finalización de la tarea, guiándole a través de los pasos secuenciales, basado en tareas. El Asistente representa una tarea de alto nivel y los paneles individuales representan subtareas necesarias para realizar la tarea.<br /><br /> Resulta útil cuando la tarea cruza los límites de la interfaz de usuario, como cuando el usuario tendría que usar varios editores y herramientas de windows para completar la tarea<br /><br /> Resulta útil cuando la tarea requiere la bifurcación<br /><br /> Resulta útil cuando la tarea contiene dependencias entre los pasos<br /><br /> Resulta útil cuando varias tareas similares con la bifurcación de una decisión que se pueden presentar en un cuadro de diálogo para reducir el número de cuadros de diálogo similares diferentes.|Inadecuado para cualquier tarea que no requiere un flujo de trabajo secuencial<br /><br /> Los usuarios pueden ser desbordado y confunde con un asistente con demasiados pasos<br /><br /> Asistentes inherentemente limitada espacio en pantalla|  
  
##### <a name="hallways-or-dashboards"></a>Los vestíbulos o paneles  
 Los vestíbulos y paneles son paneles que actúan como iniciar puntos a otros cuadros de diálogo y ventanas o cuadros de diálogo. "Pasillo" bien diseñada inmediatamente presenta sólo los más comunes opciones, comandos y configuración, que permite al usuario realizar fácilmente las tareas habituales. Como un pasillo reales proporciona entradas para tener acceso a las salas de detrás de ellos, aquí la interfaz de Usuario menos comunes se recopila en independientes "salas" (a menudo otros cuadros de diálogo) de funcionalidad relacionada que puede obtenerse acceso desde el vestíbulo principal.  
  
 Como alternativa, una interfaz de Usuario que ofrece toda la funcionalidad disponible en una sola colección, en lugar de la funcionalidad de menos comunes en ubicaciones independientes de refactorización es simplemente un panel.  
  
 ![Concepto de vestíbulo en Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")  
  
 **Concepto de vestíbulo para exponer la interfaz de Usuario adicional en Outlook**  
  
##### <a name="adaptive-ui"></a>Interfaz de Usuario adaptable  
 Mostrar u ocultar la interfaz de Usuario basada en uso o una experiencia de usuario automática notificado es otra manera de presentar la interfaz de Usuario necesaria ocultando otras partes. No se recomienda en Visual Studio como los algoritmos para decidir cuándo se debe mostrar u ocultar la interfaz de Usuario pueden ser complicados y las reglas siempre será incorrectos para un conjunto de casos.  
  
##  <a name="a-namebkmkprojectsa-projects"></a><a name="BKMK_Projects"></a> Proyectos  
  
### <a name="projects-in-the-solution-explorer"></a>Proyectos en el Explorador de soluciones  
 La mayoría de los proyectos se clasifican como basada en referencias, basada en directorio o mixto. Los tres tipos de proyectos se admiten simultáneamente en el Explorador de soluciones. La raíz de la experiencia del usuario en trabajar con proyectos tiene lugar dentro de esta ventana. Aunque los nodos de proyecto diferente son proyectos de tipo de modo mixto, directorio o referencia, hay un patrón de interacción común que se debe aplicar como punto de partida antes divergentes en patrones de usuario específicos del proyecto.  
  
 Deben ser siempre proyectos:  
  
-   Compatibilidad con la capacidad de agregar las carpetas de proyecto para organizar el contenido del proyecto  
  
-   Mantener un modelo coherente para la persistencia de un proyecto  
  
 Los proyectos también deben mantener los modelos de interacción coherente para:  
  
-   Quitar elementos de proyecto  
  
-   Guardar documentos  
  
-   Edición de propiedades de proyecto  
  
-   Edición del proyecto en una vista alternativa  
  
-   Operaciones de arrastrar y colocar  
  
### <a name="drag-and-drop-interaction-model"></a>Modelo de interacción de arrastrar y colocar  
 Proyectos normalmente clasificación por sí mismos como basada en referencias (puede conservar sólo hace referencia a los elementos de proyecto de almacenamiento), (puede conservar los elementos de proyecto sólo físicamente almacenado en la jerarquía de un proyecto), basada en directorio o mixto (puede conservar las referencias o elementos físicos). El IDE adapta a los tres tipos de proyectos simultáneamente en el **el Explorador de soluciones**.  
  
 Desde una perspectiva de arrastrar y colocar, deben aplicar las siguientes características para cada tipo de proyecto dentro de la **el Explorador de soluciones**:  
  
-   **Proyecto de referencia:** el punto clave es que el proyecto se está arrastrando en torno a una referencia a un elemento de almacenamiento. Cuando un proyecto basado en referencias actúa como origen para una operación de movimiento, sólo debe quitar la referencia al elemento del proyecto. El elemento no debe eliminarse realmente desde el disco duro. Cuando un proyecto basado en referencias actúa como un destino de una operación de mover (o copiar), debe agregar una referencia al elemento de origen original sin realizar una copia privada del elemento.  
  
-   **Proyecto basado en el directorio:** desde un punto de vista de arrastrar y colocar el proyecto arrastrando el elemento físico en lugar de una referencia. Cuando un proyecto basado en el directorio actúa como origen para una operación de movimiento, debe terminar de eliminar el elemento físico de la unidad de disco duro, así como quitar del proyecto. Cuando un proyecto basado en el directorio actúa como un destino de una operación de mover (o copiar), debe realizar una copia del elemento de origen en su ubicación de destino.  
  
-   **Proyecto de destino mixto:** desde un punto de vista de arrastrar y colocar, el comportamiento de este tipo de proyecto se basa en la naturaleza del elemento que se arrastra (una referencia a un elemento de almacenamiento) o el propio elemento. El comportamiento correcto de referencias y los elementos físicos se han descrito anteriormente.  
  
 Si hubiera un único tipo de proyecto en el **el Explorador de soluciones**, operaciones de arrastrar y colocar sería sencillas. Dado que cada sistema de proyecto tiene la capacidad para definir su propio comportamiento de arrastrar y colocar, ciertas instrucciones (basados en el comportamiento de arrastrar y colocar del explorador de Windows) se deben seguir para garantizar una experiencia de usuario predecible:  
  
-   Arrastre una sin modificar de operación en el **el Explorador de soluciones** (cuando Ctrl ni las teclas de desplazamiento se mantienen) debe tener como resultado de una operación de movimiento.  
  
-   También debería producir la operación de arrastre en una operación de movimiento.  
  
-   Operación de arrastre CTRL debería producir una operación de copia.  
  
-   Sistemas de proyectos basados en referencias y mixto admiten la noción de agregar un vínculo (o referencia) al elemento de origen. Cuando estos proyectos son el destino de una operación de arrastrar y colocar (cuando **Ctrl + Mayús** está presionada), debe dar como resultado una referencia al elemento que se agrega al proyecto  
  
 No todas las operaciones de arrastrar y colocar son razonables en combinaciones de proyectos basados en referencias, basada en directorio y mixtos. En particular, resulta problemático fingir permitir que una operación de desplazamiento entre un proyecto basado en el directorio de origen y destino basado en la referencia porque el proyecto basado en el directorio de origen tendrá que eliminar el elemento de origen tras la finalización del movimiento. El proyecto de destino basado en referencias, a continuación, terminaría con una referencia a un elemento eliminado.  
  
 También es engañosa fingir permitir que una operación de copia entre estos tipos de proyectos porque el proyecto de referencia en función de destino no debe hacer una copia independiente del elemento de origen. De forma similar, Ctrl + Mayús al arrastrar a un proyecto basado en el directorio de destino no deberían porque no puede conservar las referencias de un proyecto basado en el directorio. En casos donde no se admite la operación de arrastrar y colocar, el IDE debe impedir la eliminación y muestra al usuario el cursor no colocar (que se muestra en la siguiente tabla de puntero).  
  
 Para implementar correctamente el comportamiento de arrastrar y colocar, el proyecto de origen de la operación de arrastre necesita comunicarse su naturaleza (por ejemplo, es en directorios o referencia?) en el proyecto de destino. Esta información se indica mediante el formato de Portapapeles ofrecida por el origen. Como el origen de un arrastre (o la operación de copia del Portapapeles) debe ofrecer un proyecto bien **CF_VSREFPROJECTITEM**S o **CF_VSSTGPROJECTITEMS** respectivamente, dependiendo de si el proyecto está basado en el directorio o referencia. Ambos formatos de tienen el mismo contenido de datos, que es similar a Windows **CF_HDROP** formato salvo que son listas de cadenas, en lugar de nombres de archivo, un doble -**NULL** terminó la lista de **Projref** cadenas (tal como lo devuelve **IVsSolution::GetProjrefOfItem** o **:: GetProjrefOfProject** según corresponda).  
  
 Como el destino de una entrega (o la operación de pegar del Portapapeles), un proyecto debe aceptar ambos **CF_VSREFPROJECTITEMS** y **CF_VSSTGPROJECTITEMS**, aunque el control exacto de la operación de arrastrar y colocar varía según la naturaleza del proyecto de destino y el proyecto de origen. El proyecto de origen declara su naturaleza si ofrece **CF_VSREFPROJECTITEMS** o **CF_VSSTGPROJECTITEMS**. El destino de la operación de colocar comprende su propia naturaleza y por lo que tiene información suficiente para tomar decisiones que si un movimiento, copia, o se debe realizar el vínculo. El usuario modifica también qué operación de arrastrar y colocar debe realizarse al presionar la tecla Ctrl, MAYÚS, o tanto teclas Ctrl y MAYÚS. Es importante que el destino de colocación indicar correctamente qué operación se realizará de antemano en su **DragEnter** y **DragOver** métodos. El **el Explorador de soluciones** sabe automáticamente si el proyecto de origen y el proyecto de destino son el mismo proyecto.  
  
 Específicamente no se admite arrastrar los elementos de proyecto entre instancias de Visual Studio (por ejemplo, desde una instancia de devenv.exe a otro). El **el Explorador de soluciones** directamente deshabilita esto.  
  
 El usuario siempre debe ser capaz de determinar el efecto de una operación de arrastrar y colocar seleccionando un elemento, arrastrándolo a la ubicación de destino y observando cuál de los siguientes punteros del mouse aparece antes de quita el elemento:  
  
|Puntero del mouse|Comando|Descripción|  
|-------------------|-------------|-----------------|  
|![Icono de mouse "No colocar"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop")|No colocar|No se puede quitar el elemento a la ubicación especificada.|  
|![Icono de mouse "Copiar"](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy")|Copiar|Se copiará el elemento en la ubicación de destino.|  
|![Icono de mouse "Mover"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove")|Mover|Elemento se moverá a la ubicación de destino.|  
|![Icono de mouse "Agregar referencia"](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef")|Agregar referencia|Se agregará una referencia al elemento seleccionado en la ubicación de destino.|  
  
#### <a name="reference-based-projects"></a>Proyectos de referencia  
 En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que se deben realizar según la naturaleza de las claves de producto y el modificador de origen presionado para proyectos de destino basado en la referencia:  
  
|||Elemento de origen: o vínculo de referencia|Elemento de origen: sistema de elemento o el archivo físico (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Ningún modificador|Acción|Mover|Link|  
|Ningún modificador|Destino|Agrega la referencia al elemento original|Agrega la referencia al elemento original|  
|Ningún modificador|Origen|Referencia de eliminaciones al elemento original|Conserva el elemento original|  
|Ningún modificador|Resultado|**DROPEFFECT_MOVE** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**DROPEFFECT_LINK** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|  
|Mayús + arrastrar|Acción|Mover|No colocar|  
|Mayús + arrastrar|Destino|Agrega la referencia al elemento original|No colocar|  
|Mayús + arrastrar|Origen|Referencia de eliminaciones al elemento original|No colocar|  
|Mayús + arrastrar|Resultado|**DROPEFFECT_MOVE** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|No colocar|  
|CTRL + arrastrar|Acción|Copiar|No colocar|  
|CTRL + arrastrar|Destino|Agrega la referencia al elemento original|No colocar|  
|CTRL + arrastrar|Origen|Conserva la referencia al elemento original|No colocar|  
|CTRL + arrastrar|Resultado|**DROPEFFECT_COPY** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|No colocar|  
|Ctrl + Mayús + arrastrar|Acción|Link|Link|  
|Ctrl + Mayús + arrastrar|Destino|Agrega la referencia al elemento original|Agrega la referencia al elemento original|  
|Ctrl + Mayús + arrastrar|Origen|Conserva la referencia al elemento original|Conserva el elemento original|  
|Ctrl + Mayús + arrastrar|Resultado|**DROPEFFECT_LINK** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**DROPEFFECT_LINK** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|  
|Ctrl + Mayús + arrastrar|Nota|Igual que el comportamiento de arrastrar y colocar accesos directos en el Explorador de Windows.||  
|Cortar y pegar|Acción|Mover|Link|  
|Cortar y pegar|Destino|Agrega la referencia al elemento original|Agrega la referencia al elemento original|  
|Cortar y pegar|Origen|Conserva la referencia al elemento original|Conserva el elemento original|  
|Cortar y pegar|Resultado|Elemento permanece en la ubicación original de almacenamiento|Elemento permanece en la ubicación original de almacenamiento|  
|Copiar y pegar|Acción|Copiar|Link|  
|Copiar y pegar|Origen|Agrega la referencia al elemento original|Agrega la referencia al elemento original|  
|Copiar y pegar|Resultado|Conserva la referencia al elemento original|Conserva el elemento original|  
|Copiar y pegar|Acción|Elemento permanece en la ubicación original de almacenamiento|Elemento permanece en la ubicación original de almacenamiento|  
  
#### <a name="directory-based-projects"></a>Proyectos basados en el directorio  
 En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que se deben realizar según la naturaleza de las claves de producto y el modificador de origen presionado para proyectos basada en directorio de destino:  
  
|||Elemento de origen: o vínculo de referencia|Elemento de origen: sistema de elemento o el archivo físico (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Ningún modificador|Acción|Mover|Mover|  
|Ningún modificador|Destino|Elemento de copias en la ubicación de destino|Elemento de copias en la ubicación de destino|  
|Ningún modificador|Origen|Referencia de eliminaciones al elemento original|Referencia de eliminaciones al elemento original|  
|Ningún modificador|Resultado|**MOVER DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**MOVER DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|  
|Mayús + arrastrar|Acción|Mover|Mover|  
|Mayús + arrastrar|Destino|Elemento de copias en la ubicación de destino|Elemento de copias en la ubicación de destino|  
|Mayús + arrastrar|Origen|Referencia de eliminaciones al elemento original|Elimina el elemento de ubicación original|  
|Mayús + arrastrar|Resultado|**MOVER DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**MOVER DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|  
|CTRL + arrastrar|Acción|Copiar|Copiar|  
|CTRL + arrastrar|Destino|Elemento de copias en la ubicación de destino|Elemento de copias en la ubicación de destino|  
|CTRL + arrastrar|Origen|Conserva la referencia al elemento original|Conserva la referencia al elemento original|  
|CTRL + arrastrar|Resultado|**COPIA de DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**COPIA de DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|  
|Ctrl + Mayús + arrastrar||No colocar|No colocar|  
|Cortar y pegar|Acción|Mover|Mover|  
|Cortar y pegar|Destino|Elemento de copias en la ubicación de destino|Elemento de copias en la ubicación de destino|  
|Cortar y pegar|Origen|Referencia de eliminaciones al elemento original|Elimina el elemento de ubicación original|  
|Cortar y pegar|Resultado|Elemento permanece en la ubicación original de almacenamiento|Eliminar elemento de la ubicación original de almacenamiento|  
|Copiar y pegar|Acción|Copiar|Copiar|  
|Copiar y pegar|Destino|Agrega la referencia al elemento original|Elemento de copias en la ubicación de destino|  
|Copiar y pegar|Origen|Conserva el elemento original|Conserva el elemento original|  
|Copiar y pegar|Resultado|Elemento permanece en la ubicación original de almacenamiento|Elemento permanece en el almacenamiento de inicios de ubicación original|  
  
#### <a name="mixed-target-projects"></a>Proyectos de destino mixto  
 En la tabla siguiente se resume las operaciones de arrastrar y colocar (así como cortar, copiar y pegar) que se deben realizar según la naturaleza de las claves de producto y el modificador de origen presionado para proyectos de destino mixto:  
  
|||Elemento de origen: o vínculo de referencia|Elemento de origen: sistema de elemento o el archivo físico (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Ningún modificador|Acción|Mover|Mover|  
|Ningún modificador|Destino|Agrega la referencia al elemento original|Elemento de copias en la ubicación de destino|  
|Ningún modificador|Origen|Referencia de eliminaciones al elemento original|Referencia de eliminaciones al elemento original|  
|Ningún modificador|Resultado|**MOVER DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**MOVER DROPEFFECT_** se devuelve como acción de **:: Drop** y se elimina de la ubicación original en el almacenamiento|  
|Mayús + arrastrar|Acción|Mover|Mover|  
|Mayús + arrastrar|Destino|Agrega la referencia al elemento original|Elemento de copias en la ubicación de destino|  
|Mayús + arrastrar|Origen|Referencia de eliminaciones al elemento original|Elimina el elemento de ubicación original|  
|Mayús + arrastrar|Resultado|**MOVER DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**MOVER DROPEFFECT_** se devuelve como acción de **:: Drop** y se elimina de la ubicación original en el almacenamiento|  
|CTRL + arrastrar|Acción|Copiar|Copiar|  
|CTRL + arrastrar|Destino|Agrega la referencia al elemento original|Elemento de copias en la ubicación de destino|  
|CTRL + arrastrar|Origen|Conserva la referencia al elemento original|Conserva el elemento original|  
|CTRL + arrastrar|Resultado|**COPIA de DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**COPIA de DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|  
|Ctrl + Mayús + arrastrar|Acción|Link|Link|  
|Ctrl + Mayús + arrastrar|Destino|Agrega la referencia al elemento original|Agrega la referencia al elemento de origen original|  
|Ctrl + Mayús + arrastrar|Origen|Conserva la referencia al elemento original|Conserva el elemento original|  
|Ctrl + Mayús + arrastrar|Resultado|**VÍNCULO de DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|**VÍNCULO de DROPEFFECT_** se devuelve como acción de **:: Drop** y elemento permanece en su ubicación original en el almacenamiento|  
|Cortar y pegar|Acción|Mover|Mover|  
|Cortar y pegar|Destino|Elemento de copias en la ubicación de destino|Elemento de copias en la ubicación de destino|  
|Cortar y pegar|Origen|Referencia de eliminaciones al elemento original|Elimina el elemento de ubicación original|  
|Cortar y pegar|Resultado|Elemento permanece en la ubicación original de almacenamiento|Eliminar elemento de la ubicación original de almacenamiento|  
|Copiar y pegar|Acción|Copiar|Copiar|  
|Copiar y pegar|Destino|Agrega la referencia al elemento original|Elemento de copias en la ubicación de destino|  
|Copiar y pegar|Origen|Conserva el elemento original|Conserva el elemento original|  
|Copiar y pegar|Resultado|Elemento permanece en la ubicación original de almacenamiento|Elemento permanece en la ubicación original de almacenamiento|  
  
 Estos detalles deben tenerse en cuenta al implementar arrastrar en la **el Explorador de soluciones**:  
  
-   Diseñar para varios escenarios de selección.  
  
-   Nombres de archivo (ruta de acceso completa) deben ser únicos en el proyecto de destino o no se debe permitir la eliminación.  
  
-   Nombres de carpeta deben ser únicos (entre mayúsculas y minúsculas) en el nivel que se van a quitar.  
  
-   Existen diferencias de comportamiento entre los archivos que están abiertos o cerrados al tiempo de arrastre (que no se menciona en los escenarios anteriores).  
  
-   Archivos de nivel superior se comportan de forma ligeramente diferente a los archivos en carpetas.  
  
 Otro problema que tener en cuenta es cómo controlar las operaciones de desplazamiento en los elementos que tienen editores o diseñadores abiertos. El comportamiento esperado es como sigue (Esto se aplica a todos los tipos de proyecto):  
  
1.  Si el diseñador o editor abierto tiene cambios sin guardar, a continuación, la ventana del editor o diseñador debe estar en modo silencioso cerrada.  
  
2.  Si el diseñador o editor abierto tiene cambios no guardados, el origen de la operación de arrastrar debe esperar para que la eliminación y, a continuación, pida al usuario que guarde los cambios sin confirmar en los documentos abiertos antes de cerrar la ventana con un mensaje similar al siguiente:  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
 Esto proporciona al usuario la oportunidad de guardar el trabajo en curso antes de que el destino hace que sus copias. Un nuevo método **IVsHierarchyDropDataSource2::OnBeforeDropNotify** se ha agregado para habilitar este control.  
  
 El destino, a continuación, copiará el estado del elemento como en almacenamiento de información (sin incluir los cambios no guardados en el editor si el usuario elige **n**). Después de que el destino ha completado su copia (en **IVsHierarchyDropDataSource::Drop**), el origen tiene la oportunidad de completar la parte de la eliminación de la operación de desplazamiento (en **IVsHierarchyDropDataSource::OnDropNotify**).  
  
 Los editores sin guardar los cambios deben dejarse abiertos. Para dichos documentos sin guardar los cambios, esto significa que se llevará a cabo la parte de la copia de la operación de mover, pero se anulará la parte de eliminación. En un escenario de selección de varios cuando el usuario elige **n**, esos documentos con los cambios no guardados no puede cerrarse o quitarse, pero los que no tienen cambios no guardados deben cierra y se quita.