---
title: Creando grupos de botones reutilizables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 477014ed77b60821ad191ba6842999be6f528fee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903641"
---
# <a name="create-reusable-groups-of-buttons"></a>Crear grupos de botones reutilizables
Un grupo de comandos es una colección de comandos que siempre aparecen juntos en un menú o una barra de herramientas. Cualquier grupo de comandos se puede volver a usar asignándole a distintos menús primarios en la sección CommandPlacements del archivo *. Vsct* .

 Normalmente, los grupos de comandos contienen botones, pero también pueden contener otros menús o cuadros combinados.

## <a name="to-create-a-reusable-group-of-buttons"></a>Para crear un grupo de botones reutilizable

1. Cree un proyecto VSIX denominado `ReusableButtons` . Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Cuando se abra el proyecto, agregue una plantilla de elemento de comando personalizada denominada **ReusableCommand**. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a extensibilidad de **Visual C#**  >  **Extensibility** y seleccione **comando personalizado**. En el campo **nombre** situado en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *ReusableCommand.CS*.

3. En el archivo *. Vsct* , vaya a la sección de símbolos y busque el elemento GuidSymbol que contiene los grupos y los comandos del proyecto. Debe denominarse guidReusableCommandPackageCmdSet.

4. Agregue un IDSymbol para cada botón que vaya a agregar al grupo, como en el ejemplo siguiente.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     De forma predeterminada, la plantilla de elemento de comando crea un grupo denominado **MyMenuGroup** y un botón que tiene el nombre que proporcionó, junto con una entrada IDSymbol para cada uno.

5. En la sección grupos, cree un elemento Group que tenga los mismos atributos GUID y ID que los que se indican en la sección Symbols. También puede usar un grupo existente o usar la entrada proporcionada por la plantilla de comandos, como en el ejemplo siguiente. Este grupo aparece en el menú **herramientas**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Para crear un grupo de botones para su reutilización

1. Puede colocar un comando o un menú en un grupo utilizando el grupo como elemento primario en la definición del comando o menú, o colocando el comando o el menú en el grupo mediante la sección CommandPlacements.

     En la sección botones, defina un botón que tenga el grupo como primario, o use el botón proporcionado por la plantilla de paquete, como se muestra en el ejemplo siguiente.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Si un botón debe aparecer en más de un grupo, cree una entrada para él en la sección CommandPlacements, que debe colocarse después de la sección de comandos. Establezca los atributos GUID e ID del elemento CommandPlacement para que coincidan con los del botón que desea colocar y, a continuación, establezca el GUID y el identificador de su elemento primario en los del grupo de destino, como se muestra en el ejemplo siguiente.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > El valor del campo Priority determina la posición del comando en el nuevo grupo de comandos. Las prioridades establecidas en el elemento CommandPlacement reemplazan a las establecidas en la definición del elemento. Los comandos que tienen valores de prioridad inferiores se muestran antes que los que tienen valores de prioridad más altos. Se permiten valores de prioridad duplicados, pero no se puede garantizar la posición relativa de los comandos que tienen el mismo valor de prioridad porque es posible que el orden en el que el comando **devenv/Setup** cree la interfaz final del registro no sea coherente.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Para colocar un grupo reutilizable de botones en un menú

1. Cree una entrada en la `CommandPlacements` sección. Establezca el GUID y el identificador del `CommandPlacement` elemento en los del grupo, y establezca el GUID y el identificador principales en los de la ubicación de destino.

    La sección CommandPlacements debe colocarse justo después de la sección commands:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Un grupo de comandos se puede incluir en más de un menú. El menú primario puede ser el que ha creado, uno proporcionado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (como se describe en *ShellCmdDef. Vsct* o *SharedCmdDef. Vsct*), o uno que se define en otro VSPackage. El número de capas parentales es ilimitado, siempre que el menú primario se conecte finalmente a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o a un menú contextual que se muestre en un VSPackage.

    En el ejemplo siguiente se coloca el grupo en la barra de herramientas **Explorador de soluciones** , a la derecha de los demás botones.

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
