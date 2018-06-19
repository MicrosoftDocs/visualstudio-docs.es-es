---
title: Creación de grupos reutilizables de botones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97ee7cc2ec63a94036472ccce07b1dc9fa736504
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102985"
---
# <a name="creating-reusable-groups-of-buttons"></a>Creación de grupos reutilizable de botones
Un grupo de comandos es una colección de comandos que siempre aparecen juntas en un menú o barra de herramientas. Puede volver a utilizar cualquier grupo de comandos mediante la asignación a los menús de elemento primario diferente en la sección CommandPlacements del archivo vsct.  
  
 Grupos de comandos normalmente contienen botones, pero también pueden contener otros menús o cuadros combinados.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Para crear un grupo de botones reutilizable  
  
1.  Crear un proyecto VSIX denominado `ReusableButtons`. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de comando personalizado denominada **ReusableCommand**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para **ReusableCommand.cs**.  
  
3.  En el archivo .vsct, vaya a la sección de símbolos y busque el elemento GuidSymbol que contiene los grupos y los comandos para el proyecto. Debe llamarse guidReusableCommandPackageCmdSet.  
  
4.  Agregar un IDSymbol para cada botón que se va a agregar al grupo, como en el ejemplo siguiente.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     De forma predeterminada, la plantilla de elemento de comando crea un grupo denominado **MyMenuGroup** y un botón que tiene el nombre que ha proporcionado, junto con una entrada IDSymbol para cada uno.  
  
5.  En la sección grupos, cree un elemento de grupo que tiene los mismos atributos GUID y el ID como aquellas que se muestra en la sección de símbolos. También puede utilizar un grupo existente, o utilizar la entrada proporcionada por la plantilla del comando, como en el ejemplo siguiente. Este grupo aparece en el **herramientas** menú  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Para crear un grupo de botones para volver a usar  
  
1.  Puede colocar un comando o un menú en un grupo mediante el grupo como un elemento primario en la definición del comando o del menú o colocando el menú o el comando en el grupo mediante el uso de la sección CommandPlacements.  
  
     En la sección de botones definir un botón que tiene el grupo como su elemento primario o usar el botón que proporciona la plantilla de paquete, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Si un botón debe aparecer en más de un grupo, cree una entrada para él en la sección CommandPlacements, que se debe colocar después de la sección de comandos. Establezca los atributos GUID y el ID del elemento CommandPlacement que coincidan con las del botón que desea colocar y, a continuación, establezca el GUID y el identificador de su elemento primario a los del grupo de destino, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  El valor del campo prioridad determina la posición del comando en el nuevo grupo de comandos. Las prioridades de establecen en el CommandPlacement elemento reemplazan a las que establezca en la definición de elemento. Se muestran comandos que tienen valores de prioridad inferior antes de ejecutar comandos que tienen valores de prioridad más altos. Se permiten valores de prioridad duplicados, pero no se puede garantizar la posición relativa de los comandos que tienen el mismo valor de prioridad porque el orden en que el **devenv /setup** comando crea la interfaz de final del registro puede no ser coherente.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Poner un grupo reutilizable de botones en un menú  
  
1.  Crear una entrada en la `CommandPlacements` sección. Establece el GUID y el Id. de la `CommandPlacement` elemento a las de su grupo y establezca el elemento primario GUID y el ID a los de la ubicación de destino.  
  
     La sección CommandPlacements debe colocarse justo después de la sección de comandos:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Un grupo de comandos puede incluirse en más de un menú. El menú del elemento primario puede ser uno que ha creado, uno proporcionado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (como se describe en ShellCmdDef.vsct o SharedCmdDef.vsct), o uno que está definido en otro VSPackage. El número de niveles de relación jerárquica es ilimitado, siempre y cuando el menú primario finalmente está conectado a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o a un menú contextual que se muestra por un paquete VSPackage.  
  
     En el ejemplo siguiente se coloca el grupo el **el Explorador de soluciones** barra de herramientas a la derecha de los botones.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```
