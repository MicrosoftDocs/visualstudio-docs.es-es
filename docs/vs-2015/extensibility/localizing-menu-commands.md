---
title: Localización de los comandos de menú | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c879072b55729e249b1aecd665d6f470f4138a75
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686133"
---
# <a name="localizing-menu-commands"></a>Adaptación de comandos de menú
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede proporcionar el texto localizado para el menú y barra de herramientas de comandos mediante la creación de archivos .vsct localizado y localizar los archivos .resx para que el paquete de VS y, a continuación, actualizar los archivos de proyecto incorporar los cambios.  
  
 Para obtener información sobre cómo localizar la experiencia de instalación, consulte [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localizar los nombres de comando  
 En los paquetes VSPackage, botones de barra de herramientas y comandos de menú se definen en el archivo .vsct.  
  
1. En **el Explorador de soluciones**, cambie el nombre del archivo .vsct del *filename*.vsct a *filename*.en US.vsct.  
  
2. Realizar una copia de *filename*.en-US.vsct para cada idioma localizado.  
  
    Nombre de cada copia *filename*. *Configuración regional*.vsct, donde *configuración regional* es un nombre de referencia cultural determinada. Para obtener una lista de valores de nombre de referencia cultural, consulte [Locale IDs Assigned by Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Estos *filename*. *Configuración regional*archivos .vsct contendrá el texto del menú localizado para el paquete.  
  
3. Abra cada *filename*. *Configuración regional*archivo .vsct para localizar el texto.  
  
   1. Modificar el [ButtonText](../extensibility/buttontext-element.md) elemento valores según corresponda para el lenguaje determinado.  
  
   2. Si va a proporcionar iconos localizados, modifique la [mapa de bits](../extensibility/bitmap-element.md) valores para que apunte a los archivos de destino.  
  
      El ejemplo siguiente muestra el texto del botón para abrir una ventana de herramientas del explorador de árbol genealógico de un comando inglés y español.  
  
      [FamilyTree.en-US.vsct]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Family Tree Explorer</ButtonText>  
     </Strings>  
   </Button>  
   ```  
  
    [FamilyTree.es-ES.vsct]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Explorar el arbol genealogico</ButtonText>  
     </Strings>  
   </Button>  
  
   ```  
  
## <a name="localizing-other-text-resources"></a>Localización de otros recursos de texto  
 Recursos de texto que no sean los nombres de comando se definen en archivos de recursos (.resx).  
  
1. Cambie el nombre VSPackage.resx VSPackage.en-US.resx.  
  
2. Realice una copia del archivo VSPackage.en-US.resx para cada idioma localizado.  
  
     Nombre de cada copia de VSPackage. *Configuración regional*.resx, donde *configuración regional* es un nombre de referencia cultural determinada.  
  
3. Cambie el nombre Resources.resx Resources.en-US.resx.  
  
4. Realice una copia del archivo Resources.en-US.resx para cada idioma localizado.  
  
     Nombre de cada copia de recursos. *Configuración regional*.resx, donde *configuración regional* es un nombre de referencia cultural determinada.  
  
5. Abra cada archivo .resx para modificar los valores de cadena según corresponda para el lenguaje determinado y la referencia cultural. En el ejemplo siguiente se muestra la definición de recurso traducido de la barra de título de una ventana de herramientas.  
  
     [Resources.en-US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Incorporar recursos localizados del proyecto  
 Debe modificar el archivo assemblyinfo.cs y el archivo de proyecto para incorporar los recursos localizados.  
  
1. Desde el **propiedades** nodo **el Explorador de soluciones**, abra assemblyinfo.cs o assemblyinfo.vb en el editor.  
  
2. Agregue la siguiente entrada.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Esto establece el inglés de Estados Unidos como idioma predeterminado.  
  
3. Descargue el proyecto.  
  
4. Abra el archivo de proyecto en el editor.  
  
5. Busque el `ItemGroup` elemento que contiene `EmbeddedResource` elementos.  
  
6. En el `EmbeddedResource` elemento que llama a VSPackage.en-US.resx, reemplace el `ManifestResourceName` elemento con un `LogicalName` elemento, se establece en `VSPackage.en-US.Resources`, como se indica a continuación.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Para cada idioma localizado, copie el `EmbeddedResource` (elemento) para VsPackage.en-US y establezca el **Include** atributo y **LogicalName** elemento de la copia a la configuración regional de destino, como se muestra en la siguiente ejemplo.  
  
8. A cada localizado `VSCTCompile` elemento, agregue un `ResourceName` elemento al que apunta a `Menus.ctmenu`, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Guarde el archivo de proyecto y recargar el proyecto.  
  
10. Compile el proyecto.  
  
     Esto crea un ensamblado principal y los ensamblados de recursos para cada idioma. Para obtener información sobre la localización del proceso de implementación, consulte [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands frente a OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalización y localización](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
