---
title: Localización de los comandos de menú | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94294078ccb1dd2620127fa85acf0ae4564080dd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638035"
---
# <a name="localize-menu-commands"></a>Localizar los comandos de menú
Puede proporcionar el texto localizado para comandos de menú y barra de herramientas mediante la creación de localizado *.vsct* archivos y localizadas *.resx* archivos para el VSPackage y, a continuación, actualizar los archivos de proyecto incorporar el cambios.  
  
 Para obtener información sobre cómo localizar la experiencia de instalación, consulte [paquetes VSIX localizar](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localize-command-names"></a>Localizar los nombres de comando  
 En los paquetes VSPackage, los botones de barra de herramientas y comandos de menú se definen en el *.vsct* archivo.  
  
1.  En **el Explorador de soluciones**, cambie el nombre de la *.vsct* de archivos de *filename.vsct* a *filename.en US.vsct*.  
  
2.  Realizar una copia de *filename.en US.vsct* para cada idioma localizado.  
  
     Nombre de cada copia *nombre de archivo. {} Configuración regional} .vsct*, donde *{Locale}* es un nombre de referencia cultural determinada. Para obtener una lista de valores de nombre de referencia cultural, consulte [identificadores de configuración regional asignados por Microsoft](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Estos *nombre de archivo. Locale.vsct* archivos contendrá el texto del menú localizado para el paquete.  
  
3.  Abra cada *nombre de archivo. Locale.vsct* archivos para localizar el texto.  
  
    1.  Modificar el [ButtonText](../extensibility/buttontext-element.md) elemento valores según corresponda para el lenguaje determinado.  
  
    2.  Si va a proporcionar iconos localizados, modifique la [mapa de bits](../extensibility/bitmap-element.md) valores para que apunte a los archivos de destino.  
  
     El ejemplo siguiente muestra el texto del botón para abrir una ventana de herramientas del explorador de árbol genealógico de un comando inglés y español.  
  
     [*FamilyTree.en US.vsct*]  
  
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
  
     [*FamilyTree.es ES.vsct*]  
  
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
  
## <a name="localize-other-text-resources"></a>Localizar a otros recursos de texto  
 Recursos de texto que no sean los nombres de comando se definen en el recurso (*.resx*) los archivos.  
  
1.  Cambiar el nombre de *VSPackage.resx* a *VSPackage.en-US.resx*.  
  
2.  Realizar una copia de la *VSPackage.en-US.resx* archivo para cada idioma localizado.  
  
     Nombre de cada copia *VSPackage. {} Configuración regional} .resx*, donde *{Locale}* es un nombre de referencia cultural determinada.  
  
3.  Cambiar el nombre de *Resources.resx* a *Resources.en-US.resx*.  
  
4.  Realizar una copia de la *Resources.en-US.resx* archivo para cada idioma localizado.  
  
     Nombre de cada copia *recursos. {} Configuración regional} .resx*, donde *{Locale}* es un nombre de referencia cultural determinada.  
  
5.  Abra cada *.resx* archivo para modificar la cadena de valores según corresponda para el lenguaje determinado y la referencia cultural. En el ejemplo siguiente se muestra la definición de recurso traducido de la barra de título de una ventana de herramientas.  
  
     [*Resources.en-US.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [*Resources.es-ES.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporate-localized-resources-into-the-project"></a>Incorporar recursos localizados en el proyecto  
 Debe modificar el *assemblyinfo.cs* archivo y el archivo de proyecto para incorporar los recursos localizados.  
  
1.  Desde el **propiedades** nodo **el Explorador de soluciones**, abra *assemblyinfo.cs* o *assemblyinfo.vb* en el editor.  
  
2.  Agregue la siguiente entrada.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Esto establece el inglés de Estados Unidos como idioma predeterminado.  
  
3.  Descargue el proyecto.  
  
4.  Abra el archivo de proyecto en el editor.  
  
5.  Busque el `ItemGroup` elemento que contiene `EmbeddedResource` elementos.  
  
6.  En el `EmbeddedResource` elemento que llama a *VSPackage.en-US.resx*, reemplace el `ManifestResourceName` elemento con un `LogicalName` elemento, se establece en `VSPackage.en-US.Resources`, como se indica a continuación.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Para cada idioma localizado, copie el `EmbeddedResource` (elemento) para `VsPackage.en-US`y establezca el **Include** atributo y **LogicalName** elemento de la copia a la configuración regional de destino, como se muestra en la siguiente ejemplo.  
  
8.  A cada localizado `VSCTCompile` elemento, agregue un `ResourceName` elemento al que apunta a `Menus.ctmenu`, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Guarde el archivo de proyecto y recargar el proyecto.  
  
10. Compile el proyecto.  
  
     Esto crea un ensamblado principal y los ensamblados de recursos para cada idioma. Para obtener información sobre la localización del proceso de implementación, consulte [paquetes VSIX localizar](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Vea también  
 [Extender los menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands frente a OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)