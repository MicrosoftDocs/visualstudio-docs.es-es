---
title: Creación de grupos de botones reutilizables ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739464"
---
# <a name="create-reusable-groups-of-buttons"></a>Crear grupos reutilizables de botones
Un grupo de comandos es una colección de comandos que siempre aparecen juntos en un menú o barra de herramientas. Cualquier grupo de comandos se puede reutilizar asignándolo a diferentes menús primarios en la sección CommandPlacements del archivo *.vsct.*

 Los grupos de comandos suelen contener botones, pero también pueden contener otros menús o cuadros combinados.

## <a name="to-create-a-reusable-group-of-buttons"></a>Para crear un grupo reutilizable de botones

1. Cree un proyecto `ReusableButtons`VSIX denominado . Para obtener más información, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizada denominada **ReusableCommand**. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a**Extensibilidad** de **Visual C-** > y seleccione **Comando personalizado**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *ReusableCommand.cs*.

3. En el archivo *.vsct,* vaya a la sección Símbolos y busque el elemento GuidSymbol que contiene grupos y comandos para el proyecto. Debe denominarse guidReusableCommandPackageCmdSet.

4. Agregue un IDSymbol para cada botón que agregará al grupo, como en el ejemplo siguiente.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     De forma predeterminada, la plantilla de elemento de comando crea un grupo denominado **MyMenuGroup** y un botón que tiene el nombre que proporcionó, junto con una entrada IDSymbol para cada uno.

5. En la sección Grupos, cree un elemento Group que tenga los mismos atributos GUID e ID que los especificados en la sección Símbolos. También puede utilizar un grupo existente o la entrada proporcionada por la plantilla de comando, como en el ejemplo siguiente. Este grupo aparece en el menú **Herramientas**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Para crear un grupo de botones para reutilizarlos

1. Puede colocar un comando o menú en un grupo utilizando el grupo como elemento primario en la definición del comando o menú, o colocando el comando o menú en el grupo mediante la sección CommandPlacements.

     En la sección Botones, defina un botón que tenga el grupo como elemento primario o use el botón proporcionado por la plantilla de paquete, como se muestra en el ejemplo siguiente.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Si un botón debe aparecer en más de un grupo, cree una entrada para él en la sección CommandPlacements, que debe colocarse después de la sección Commands. Establezca los atributos GUID e ID del elemento CommandPlacement para que coincidan con los del botón que desea colocar y, a continuación, establezca el GUID y el identificador de su elemento Primario en los del grupo de destino, como se muestra en el ejemplo siguiente.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > El valor del campo Prioridad determina la posición del comando en el nuevo grupo de comandos. Las prioridades establecidas en el elemento CommandPlacement reemplazan las establecidas en la definición del elemento. Los comandos que tienen valores de prioridad más bajos se muestran antes que los comandos que tienen valores de prioridad más altos. Se permiten valores de prioridad duplicados, pero la posición relativa de los comandos que tienen el mismo valor de prioridad no se puede garantizar porque el orden en el que el comando **devenv /setup** crea la interfaz final del registro puede no ser coherente.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Para poner un grupo reutilizable de botones en un menú

1. Cree una entrada `CommandPlacements` en la sección. Establezca el GUID y `CommandPlacement` el identificador del elemento en los del grupo y establezca el GUID principal y el identificador en los de la ubicación de destino.

    La sección CommandPlacements debe colocarse justo después de la sección Comandos:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Un grupo de comandos se puede incluir en más de un menú. El menú primario puede ser uno que ha [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] creado, uno proporcionado por (como se describe en *ShellCmdDef.vsct* o *SharedCmdDef.vsct*), o uno que se define en otro VSPackage. El número de capas de elementos primarios es ilimitado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] siempre y cuando el menú primario se conecte finalmente a o a un menú contextual que se muestra mediante un VSPackage.

    En el ejemplo siguiente se coloca el grupo en la barra de herramientas **del Explorador** de soluciones, a la derecha de los otros botones.

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
