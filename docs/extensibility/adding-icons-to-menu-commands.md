---
title: "Agregar iconos a los comandos de men&#250; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "iconos [Visual Studio], agregar barras de herramientas"
  - "barras de herramientas [Visual Studio], agregar iconos a los comandos"
  - "Agregar iconos de comandos [Visual Studio]"
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Agregar iconos a los comandos de men&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los comandos pueden aparecer en los menús y barras de herramientas. En las barras de herramientas, es habitual para un comando que se mostrará con un icono \(para ahorrar espacio\) mientras en menús normalmente aparece un comando con un icono y el texto.  
  
 Iconos son 16 píxeles de ancho por 16 píxeles de alto y pueden ser la profundidad de color de 8 bits \(256 colores\) o la profundidad de color de 32 bits \(color verdadero\). se prefieren los iconos de colores de 32 bits. Normalmente se organizan los iconos en una fila horizontal de un mapa de bits único, aunque se permiten varios mapas de bits. Este mapa de bits se declara en el archivo .vsct junto con los iconos individuales disponibles en el mapa de bits. Consulte la referencia para la [Elemento de mapas de bits](../extensibility/bitmaps-element.md) para obtener más detalles.  
  
## Agregar un icono a un comando  
 El siguiente procedimiento se supone que tiene un proyecto de VSPackage existente con un comando de menú. Para averiguar cómo hacerlo, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Crear un mapa de bits con una profundidad de color de 32 bits. Siempre es un icono de 16 x 16 para que este mapa de bits debe ser de 16 píxeles de alto y un múltiplo de 16 píxeles de ancho.  
  
     Cada icono se coloca en el mapa de bits contiguos en una sola fila. Utilice el canal alfa para indicar los lugares de transparencia de cada icono.  
  
     Si utiliza una profundidad de color de 8 bits, utilice magenta, `RGB(255,0,255)`, como la transparencia. Sin embargo, los iconos de color de 32 bits se prefieren.  
  
2.  Copie el archivo de icono en el directorio de recursos en el proyecto de VSPackage. En el Explorador de soluciones, agregue el icono al proyecto. \(Seleccionar recursos y en el menú contextual, haga clic en Agregar y, a continuación, elemento existente y seleccione el archivo de icono\).  
  
3.  Abra el archivo .vsct en el editor.  
  
4.  Agregar un `GuidSymbol` elemento con un nombre de **testIcon**. Cree un GUID \(**Herramientas \/ crear GUID**, a continuación, seleccione **formato del registro** y haga clic en Copiar\) y péguelo en el `value` atributo. El resultado debería tener este aspecto:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Agregar un `<IDSymbol>` para el icono. El `name` atributo es el identificador del icono y el `value` indica su posición en la banda, si existe. Si hay un solo icono, agrega 1. El resultado debería tener este aspecto:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Crear un `<Bitmap>` en la `<Bitmaps>` sección del archivo .vsct para representar el mapa de bits que contiene los iconos.  
  
    -   Establecer el `guid` valor el nombre de la `<GuidSymbol>` elemento creado en el paso anterior.  
  
    -   Establecer el `href` valor a la ruta de acceso relativa del archivo de mapa de bits \(en este caso **recursos\\ \< nombre de archivo de icono \>**.  
  
    -   Establecer el `usedList` valor para el IDSymbol que creó anteriormente. Este atributo especifica una lista delimitada por comas de los iconos que se usará en el paquete VSPackage. Iconos no están en la lista son la compilación del formulario excluidos.  
  
         El bloque de mapa de bits debe tener este aspecto:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Existente `<Button>` elemento, establezca la `Icon` elemento a los valores de GUIDSymbol y IDSymbol que creó anteriormente. Este es un ejemplo de un elemento Button con estos valores:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  El icono de prueba. Compile la solución y comience la depuración. En la instancia experimental, busque el comando. Debe mostrar el icono que agregó.  
  
## Vea también  
 [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)   
 [Referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md)