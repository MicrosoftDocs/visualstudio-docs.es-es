---
title: "IntelliSense para Visual C# | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [C#]"
  - "IntelliSense [J#]"
  - "Visual C#, IntelliSense"
ms.assetid: 79ca304d-dc1e-4dc9-a2a6-7808df2e588e
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# IntelliSense para Visual C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual C\# IntelliSense está disponible cuando se codifica en el editor y mientras se depura en la ventana de comandos [Modo Inmediato](../ide/reference/immediate-window.md).  
  
## Listas de finalización  
 Las listas de finalización de IntelliSense en Visual C\# contienen, entre otros, los tokens de la lista de miembros y palabra completa.  Proporciona acceso rápido a:  
  
-   miembros de un tipo o espacio de nombres;  
  
-   variables, comandos y nombres de funciones;  
  
-   [fragmentos de código](#CodeSnippets);  
  
-   [palabras clave del lenguaje](#Keywords);  
  
-   [métodos de extensión.](#ExtensionMethods)  
  
 La lista de finalización en C\# también es lo suficientemente inteligente como para filtrar los tokens irrelevantes y hacer una selección previa de un token en función del contexto.  Para obtener más información, consulte los artículos sobre las [Listas de finalización filtradas en C\#](../misc/filtered-completion-lists-in-csharp.md) y los [Elementos de la lista de finalización preseleccionada en C\#](../misc/pre-selected-completion-list-items-in-csharp.md).  
  
###  <a name="CodeSnippets"></a> Fragmentos de código en listas de finalización  
 En Visual C\#, la lista de finalización incluye fragmentos de código para facilitar la inserción en el programa de cuerpos de código predefinidos.  Los fragmentos de código aparecen en la lista de finalización como el [elemento Shortcut \(fragmentos de código Intellisense\)](http://msdn.microsoft.com/es-es/052cc97a-5c70-42f8-b398-4c3adf670cfa) del fragmento de código.  Para obtener más información acerca de los fragmentos de código que están disponibles en Visual C\# de forma predeterminada, consulte el artículo sobre la [Fragmentos de código de Visual C\#](../ide/visual-csharp-code-snippets.md).  
  
###  <a name="Keywords"></a> Palabras clave de lenguaje en listas de finalización  
 En Visual C\#, la lista de finalización también incluye palabras clave del lenguaje.  Para obtener más información acerca de las palabras claves del lenguaje C\#, vea el artículo sobre [Palabras clave de C\#](/dotnet/csharp/language-reference/keywords/index).  
  
###  <a name="ExtensionMethods"></a> Métodos de extensión en listas de finalización  
 En Visual C\#, la lista de finalización incluye métodos de extensión que están en el ámbito.  
  
> [!NOTE]
>  La lista de finalización no muestra todos los métodos de extensión para objetos <xref:System.String>.  
  
 Los métodos de extensión usan un icono diferente del que usan los métodos de instancia.  Para obtener una lista de los iconos, vea el artículo sobre [Iconos de la Vista de clases y del Examinador de objetos](../ide/class-view-and-object-browser-icons.md).  Cuando un método de instancia y un método de extensión que tienen el mismo nombre se encuentran ambos en el ámbito, la lista de finalización muestra el icono de método de extensión.  
  
### Listas de finalización filtradas  
 IntelliSense usa filtros para quitar los miembros innecesarios de la lista de finalización.  
  
 Visual C\# filtra las listas de finalización que aparecen para estos elementos:  
  
-   **Interfaces y clases base.** IntelliSense quita automáticamente los elementos de las listas de finalización de clase base e interfaz, tanto en las listas de interfaz y base de declaración de clases como en las listas de restricciones.  Por ejemplo, las enumeraciones no aparecen en la lista de finalización de las clases base porque las enumeraciones no se pueden usar para clases base.  La lista de finalización de clases base solo contiene interfaces y espacios de nombres.  Si selecciona un elemento en la lista y luego escribe una coma, IntelliSense quita las clases base de la lista de finalización porque Visual C\# no admite herencia múltiple.  El mismo comportamiento se produce con las cláusulas de restricción.  
  
-   **Atributos**: cuando se aplica un atributo a un tipo, la lista de finalización se filtra para incluir únicamente los tipos que descienden de los espacios de nombres que contienen esos tipos, como <xref:System.Attribute>.  
  
-   Operadores `as` e `is`  
  
-   **Cláusulas catch**  
  
-   **Inicializadores de objeto:** solo los miembros que se pueden inicializar aparecerán en la lista de finalización.  
  
-   **Palabra clave new**: si se escribe `new` y luego se presiona la barra espaciadora, aparece una lista de finalización.  Automáticamente se selecciona un elemento de la lista, que variará según el contexto del código.  Por ejemplo, se seleccionan automáticamente elementos en la lista de finalización para las declaraciones y las instrucciones return de métodos.  
  
-   **Operadores as e is:** cuando se presiona la barra espaciadora después de haber escrito la palabra clave `as` o `is`, aparece automáticamente una lista de finalización filtrada.  
  
-   Eventos: i se escribe la palabra clave `event`, la lista de finalización solo contiene tipos delegados.  
  
-   La ayuda de parámetros se ordena automáticamente por la primera sobrecarga de método que coincida con los parámetros que se especifican.  Si existen varias sobrecargas de método, puede usar las flechas arriba y abajo para desplazarse a la siguiente sobrecarga posible de la lista.  
  
## Miembros usados más recientemente  
 IntelliSense recuerda los miembros que se han seleccionado recientemente en el cuadro emergente [Lista de miembros](../ide/using-intellisense.md) para autocompletar nombres de objetos.  La siguiente vez que utiliza la lista de miembros, los miembros utilizados más recientemente se muestran en la parte superior.  El historial de los miembros usados recientemente se borra entre cada sesión del IDE.  
  
## override  
 Cuando escriba [invalidar](/dotnet/csharp/language-reference/keywords/override) y, a continuación, presione la BARRA ESPACIADORA, IntelliSense muestra todos los miembros de la clase base válidos que se pueden reemplazar en un cuadro de lista emergente.  Si se escribe el tipo de valor devuelto del método después de `override`, IntelliSense mostrará solo los métodos que devuelven el mismo tipo.  Cuando IntelliSense no encuentra ninguna coincidencia, mostrará todos los miembros de clase base.  
  
## Generación automática de código  
  
### Agregar using  
 La operación Agregar using de IntelliSense permite mantener el foco en el código que se escribe en lugar tener que cambiar el foco a otra parte del código.  
  
 Para iniciar la operación Agregar using, coloque el cursor en una referencia de tipo que no se pueda resolver.  Por ejemplo, al crear una aplicación de consola y, a continuación, agregar `XmlTextReader` al cuerpo del método `Main`, aparecerá una etiqueta inteligente bajo el carácter situado en el extremo derecho de `XmlTextReader`, dado que aparece como una referencia de tipo que no se puede resolver.  
  
 ![Agregar imagen de uso de etiquetas inteligentes](../ide/media/addusesmart.png "AddUseSmart")  
  
 A continuación, puede invocar Agregar using seleccionándola en el submenú **Resolver** del menú **IntelliSense** o el menú contextual, o invocando Agregar using mediante la etiqueta inteligente.  La etiqueta inteligente sólo está visible cuando el cursor se coloca encima del tipo sin enlazar o junto a él.  
  
 ![Agregar imagen expandida de uso de etiquetas inteligentes](../ide/media/addusesmartexp.gif "AddUseSmartExp")  
  
### Organizar instrucciones Using  
 Las opciones **Organizar instrucciones Using** ordenan y quitan declaraciones `using` y `extern` sin cambiar el comportamiento del código fuente.  Con el tiempo, los archivos de origen se inflan y resultan difíciles de leer debido a la presencia de directivas `using` innecesarias y desorganizadas.  Las opciones **Organizar instrucciones Using** compactan el código fuente mediante la eliminación de las `using` no utilizadas; además, las ordenan, lo que mejora su legibilidad.  
  
 Para ver las opciones disponibles en el IDE de Visual Studio, vaya al menú **Edición**, apunte a **IntelliSense** y, a continuación, apunte a **Organizar instrucciones Using**.  El IDE proporciona las siguientes opciones para organizar y quitar directivas `usings`:  
  
### Implementar interfaz  
 IntelliSense proporciona una opción para ayudar a implementar un [interfaz](/dotnet/csharp/language-reference/keywords/interface) mientras trabaja en el Editor de código.  Normalmente, para implementar una interfaz correctamente debe crear una declaración de método para cada miembro de la interfaz de su clase.  Con IntelliSense, después de escribir el nombre de una interfaz en una declaración de clase, se muestra una etiqueta inteligente.  La etiqueta inteligente ofrece la opción de implementar la interfaz automáticamente, mediante denominación explícita o implícita.  Con la denominación explícita, las declaraciones de método llevan el nombre de la interfaz. Con la denominación implícita, las declaraciones de método no indican la interfaz a la que pertenecen.  Puede tener acceso a un método de interfaz denominada explícitamente a través de una instancia de interfaz, pero no a través de una instancia de clase.  Para obtener más información, consulte [Implementación explícita de interfaz](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).  
  
 La opción Implementar interfaz generará el número mínimo de códigos auxiliares del método necesario para satisfacer la interfaz.  Si una clase base implementa partes de la interfaz, esos códigos auxiliares no se volverán a generar.  
  
### Implementar una clase base abstracta  
 IntelliSense proporciona una opción útil para implementar miembros de una clase base abstracta de forma automática mientras se trabaja en el Editor de código.  Normalmente, la implementación de miembros de una clase base abstracta requiere la creación de una nueva definición de método para cada método de la clase base abstracta en la clase derivada.  Con IntelliSense, después de escribir el nombre de una clase base abstracta en una declaración de clase, se muestra una etiqueta inteligente.  La etiqueta inteligente ofrece la opción de implementar los métodos de la clase base automáticamente.  
  
 El código auxiliar del método generado por la característica Implementar clases base abstractas está modelado por el fragmento de código definido en el archivo MethodStub.snippet.  Los fragmentos de código son modificables.  Para obtener más información, consulte [Tutorial: Crear un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md).  
  
### Generar a partir del uso  
 La característica **Generar a partir del uso** le permite usar clases y miembros antes de definirlos.  Puede generar un código auxiliar para cualquier clase, constructor, método, propiedad, campo o enumeración que desee usar pero aún no haya definido.  Puede generar nuevos tipos y miembros sin abandonar su ubicación actual en el código.  Esto minimiza la interrupción del flujo de trabajo.  
  
 Aparece un subrayado ondulado debajo de cada identificador no definido.  Cuando se sitúa el puntero del mouse sobre el identificador, aparece un mensaje de error en una ventana de información rápida.  
  
 Para mostrar las opciones adecuadas, puede usar uno de los procedimientos siguientes:  
  
-   Haga clic en el identificador no definido.  Aparece un subrayado corto bajo el carácter más a la izquierda.  Sitúe el puntero del mouse sobre el subrayado corto y aparecerá una etiqueta inteligente \(un icono\).  Haga clic en la etiqueta inteligente.  
  
-   Haga clic en el identificador no definido y, a continuación, presione CTRL\+.  \(punto\).  
  
-   Haga clic con el botón secundario en el identificador no definido y, a continuación, haga clic en **Generar**.  
  
 Las opciones que aparecen pueden incluir lo siguiente:  
  
-   **Generar código auxiliar de propiedad**  
  
-   **Generar código auxiliar de campo**  
  
-   **Generar código auxiliar del método**  
  
-   **Generar clase**  
  
-   **Generar nuevo tipo** \(para una clase, estructura, interfaz o enumeración\)  
  
## Generar controladores de eventos  
 En el Editor de código, IntelliSense puede ayudarle a enlazar métodos \(controladores de eventos\) a campos de evento.  
  
 Al escribir el operador `+=` después de un campo de evento en un archivo .cs, IntelliSense le presenta la opción de presionar la tecla TAB.  Al hacerlo, se inserta una nueva instancia de un delegado que apunta al método que controlará el evento.  
  
 ![Botón Enlazar automáticamente](../ide/media/vxautohookup.gif "vxAutoHookUp")  
  
 Si presiona TAB, IntelliSense completa la instrucción automáticamente y muestra la referencia del controlador de eventos como texto seleccionado en el Editor de código.  Para completar el enlace de eventos automático, IntelliSense le indicará que presione la tecla TAB para crear un código auxiliar vacío para el controlador de eventos.  
  
 ![Generar controlador de eventos](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")  
  
> [!NOTE]
>  Si un nuevo delegado creado por IntelliSense hace referencia a un controlador de eventos existente, IntelliSense comunica esta información en la información rápida.  A continuación, puede modificar la referencia. El texto estará ya seleccionado en el Editor de código.  De lo contrario, el enlace de eventos automático se habrá completado en este momento.  
  
 Si presiona TAB, IntelliSense crea el código auxiliar de un método con la firma correcta y coloca el cursor en el cuerpo del controlador de eventos.  
  
> [!NOTE]
>  Utilice el comando **Navegar hacia atrás** del menú **Ver** \(CTRL\+\-\) para volver a la instrucción de enlace de eventos.  
  
 La tarea siguiente muestra cómo IntelliSense enlaza automáticamente un controlador de eventos denominado `button1_Click` a un campo de evento denominado `button1.Click`.  
  
## Vea también  
 [IDE de Visual Studio](../ide/visual-studio-ide.md)