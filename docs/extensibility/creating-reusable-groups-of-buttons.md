---
title: Creación de grupos reutilizables de botones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe0d5c3dd55380587f8f5f1c6477ee8c53bf1156
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051666"
---
# <a name="create-reusable-groups-of-buttons"></a>Creación de grupos reutilizables de botones
Un grupo de comandos es una colección de comandos que siempre aparecen juntas en un menú o barra de herramientas. Cualquier grupo de comandos puede volver a utilizarse asignándola a los menús de primarios diferentes en la sección CommandPlacements de la *.vsct* archivo.

 Grupos de comandos suelen contengan botones, pero también puede contener otros menús o cuadros combinados.

## <a name="to-create-a-reusable-group-of-buttons"></a>Para crear un grupo de botones reutilizable

1. Cree un proyecto VSIX denominado `ReusableButtons`. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizado denominada **ReusableCommand**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C#** > **extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para *ReusableCommand.cs*.

3. En el *.vsct* de archivos, vaya a la sección Symbols y busque el elemento GuidSymbol que contiene los grupos y los comandos para el proyecto. Se debe denominarse guidReusableCommandPackageCmdSet.

4. Agregue un IDSymbol para cada botón que va a agregar al grupo, como se muestra en el ejemplo siguiente.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     De forma predeterminada, la plantilla de elemento de comando crea un grupo denominado **MyMenuGroup** y un botón que tiene el nombre que ha proporcionado, junto con una entrada IDSymbol para cada uno.

5. En la sección grupos, crear un elemento de grupo que tiene los mismos atributos identificadores ID y GUID como los que figura en la sección Symbols. También puede usar un grupo existente, o utilice la entrada proporcionada por la plantilla del comando, como en el ejemplo siguiente. Este grupo aparezca en el **herramientas** menú

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Para crear un grupo de botones para su reutilización

1. Puede colocar un menú o un comando en un grupo mediante el grupo como un elemento primario en la definición del menú o comando, o colocando el menú o un comando en el grupo mediante el uso de la sección CommandPlacements.

     En la sección de botones definir un botón que tiene el grupo como su elemento primario o usar el botón que se proporciona mediante la plantilla de paquete, tal como se muestra en el ejemplo siguiente.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Si un botón debe aparecer en más de un grupo, crear una entrada para él en la sección CommandPlacements, que se debe colocar después de la sección de comandos. Establezca los atributos ID y GUID del elemento CommandPlacement que coincidan con las del botón que desea colocar y, a continuación, establezca el GUID y el identificador de su elemento primario a los del grupo de destino, tal como se muestra en el ejemplo siguiente.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    >  El valor del campo prioridad determina la posición del comando en el nuevo grupo de comandos. Establecen prioridades en el CommandPlacement elemento reemplazan a las establecidas en la definición de elemento. Se muestran los comandos que tienen valores de prioridad inferior antes de ejecutar comandos que tienen los valores de prioridad más altos. Se permiten valores de prioridad duplicados, pero no se puede garantizar la posición relativa de los comandos que tienen el mismo valor de prioridad porque el orden en que el **devenv /setup** comando crea la interfaz de final del registro es posible que no sea coherente.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Poner un grupo reutilizable de botones en un menú

1. Crear una entrada en el `CommandPlacements` sección. Establece el GUID y el identificador de la `CommandPlacement` elemento a las de su grupo y establezca el elemento primario GUID e identificador con los de la ubicación de destino.

    La sección CommandPlacements debe colocarse justo después de la sección de comandos:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Un grupo de comandos puede incluirse en más de un menú. El menú primario puede ser uno que ha creado, uno proporcionado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (como se describe en *ShellCmdDef.vsct* o *SharedCmdDef.vsct*), o uno que se define en otro VSPackage. El número de capas de la relación jerárquica es ilimitado, siempre y cuando el menú primario finalmente está conectado a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o a un menú contextual que se muestra un VSPackage.

    El ejemplo siguiente coloca el grupo el **el Explorador de soluciones** barra de herramientas a la derecha de los otros botones.

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
