---
title: "Creaci&#243;n de grupos reutilizables de botones | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "grupos de botones, creación de VSPackages"
  - "VSPackages, crear grupos de botones reutilizables"
  - "botones, crear grupos reutilizables"
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 44
caps.handback.revision: 44
ms.author: "gregvanl"
manager: "ghogen"
---
# Creaci&#243;n de grupos reutilizables de botones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un grupo de comandos es una colección de comandos que siempre aparecen juntos en un menú o barra de herramientas. Cualquier grupo de comandos se puede reutilizar asignando a menús principales en la sección CommandPlacements del archivo vsct.  
  
 Normalmente, los grupos de comandos contienen botones, pero también pueden contener otros menús o cuadros combinados.  
  
### Para crear un grupo reutilizable de botones  
  
1.  Cree un proyecto VSIX denominado `ReusableButtons`. Para obtener más información, consulta [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de comando personalizado denominada **ReusableCommand**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, el nombre del archivo de comandos **ReusableCommand.cs**.  
  
3.  En el archivo .vsct, vaya a la sección de símbolos y busque el elemento GuidSymbol que contiene los grupos y comandos para el proyecto. Debe llamarse guidReusableCommandPackageCmdSet.  
  
4.  Agregar un IDSymbol para cada botón que se va a agregar al grupo, como en el ejemplo siguiente.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="ReusableCommandId" value="0x0100" /> <IDSymbol name="SecondReusableCommandId" value="0x0200" /> </GuidSymbol>  
    ```  
  
     De forma predeterminada, la plantilla de elemento de comando crea un grupo denominado **MyGroup** y un botón que tiene el nombre que ha proporcionado, junto con una entrada IDSymbol para cada uno.  
  
5.  En la sección grupos, cree un elemento de grupo que tiene los mismos atributos GUID e ID, como los que figuran en la sección de símbolos. También puede usar un grupo existente, o utilizar la entrada proporcionada por la plantilla del comando, como en el ejemplo siguiente. Este grupo aparece en el **herramientas** menú  
  
    ```xml  
    <Groups> <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/> </Group> </Groups>  
    ```  
  
### Para crear un grupo de botones para volver a utilizar  
  
1.  Puede colocar un menú o un comando en un grupo mediante el grupo primario en la definición del comando o menú, o colocando el menú o el comando en el grupo mediante la sección CommandPlacements.  
  
     En la sección de botones definir un botón que tenga el grupo como su elemento primario o utilice el botón proporcionada por la plantilla de paquete, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> <Icon guid="guidImages" id="bmpPic1" /> <Strings> <ButtonText>Invoke ReusableCommand</ButtonText> </Strings> </Button>  
    ```  
  
2.  Si un botón debe aparecer en más de un grupo, debe crear una entrada para él en la sección CommandPlacements, que debe colocarse después de la sección de comandos. Establecer los atributos GUID y el ID del elemento CommandPlacement que coincidan con las del botón que desea colocar y, a continuación, establezca el GUID y el identificador de su elemento primario a los del grupo de destino, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> </CommandPlacement> </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  El valor del campo prioridad determina la posición del comando en el nuevo grupo de comandos. Establecen prioridades en el CommandPlacement elemento invalidarlos establecidos en la definición de elemento. Se muestran comandos que tienen valores de prioridad inferior antes de ejecutar comandos que tienen valores de prioridad más altos. Se permiten los valores de prioridad duplicados, pero no se puede garantizar la posición relativa de los comandos que tienen el mismo valor de prioridad porque el orden en que el **devenv \/setup** comando crea la última interfaz desde el registro puede no ser coherente.  
  
### Poner un grupo reutilizable de botones en un menú  
  
1.  Crear una entrada en la `CommandPlacements` sección. Establece el GUID y el Id. de la `CommandPlacement` elemento del grupo y establecer el elemento primario GUID e identificadores a los de la ubicación de destino.  
  
     La sección CommandPlacements debería colocarse justo después de la sección de comandos:  
  
    ```xml  
    <CommandTable> ... <Commands>... </Commands> <CommandPlacements>... </CommandPlacements> ... </CommandTable>  
    ```  
  
     Un grupo de comandos puede incluirse en más de un menú. El menú primario puede ser una que ha creado, uno proporcionado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(como se describe en ShellCmdDef.vsct o SharedCmdDef.vsct\), o uno que está definido en otro VSPackage. El número de niveles de relación jerárquica es ilimitado, siempre y cuando el menú primario finalmente está conectado a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o a un menú contextual que se muestra en un VSPackage.  
  
     En el ejemplo siguiente se coloca el grupo en el **el Explorador de soluciones** barra de herramientas a la derecha de los botones.  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/> </CommandPlacement> </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup" priority="0x605"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" /> </CommandPlacement> </CommandPlacements>  
  
    ```