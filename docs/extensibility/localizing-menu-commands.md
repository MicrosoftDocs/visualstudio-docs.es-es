---
title: Localizar los comandos de menú | Documentos de Microsoft
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
ms.openlocfilehash: d4fd8f2b42464b31c71b2983dd3e5c66f4a03351
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142713"
---
# <a name="localizing-menu-commands"></a>Localizar los comandos de menú
Puede proporcionar el texto localizado para el menú y barra de herramientas de comandos mediante la creación de archivos de vsct localizado y adaptado .resx (archivos) para que el paquete de VS y, a continuación, actualizar los archivos de proyecto incorporar los cambios.  
  
 Para obtener información sobre cómo localizar la experiencia de instalación, consulte [adaptar paquetes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localizar los nombres de comando  
 En los paquetes VSPackage, botones de barra de herramientas y comandos de menú se definen en el archivo .vsct.  
  
1.  En **el Explorador de soluciones**, cambie el nombre del archivo .vsct del *filename*.vsct a *filename*.en-US.vsct.  
  
2.  Realizar una copia de *filename*.en-US.vsct para cada uno de los idiomas localizados.  
  
     El nombre de cada copia *filename*. *Configuración regional*.vsct, donde *configuración regional* es un nombre de referencia cultural determinada. Para obtener una lista de valores de nombre de referencia cultural, consulte [Locale IDs Assigned by Microsoft](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Estos *filename*. *Configuración regional*archivos .vsct contendrá el texto del menú localizada para el paquete.  
  
3.  Abra cada *filename*. *Configuración regional*archivo .vsct para localizar el texto.  
  
    1.  Modificar el [ButtonText](../extensibility/buttontext-element.md) elemento valores según corresponda para el lenguaje determinado.  
  
    2.  Si va a proporcionar iconos localizados, modifique la [mapa de bits](../extensibility/bitmap-element.md) valores para que señalen a los archivos de destino.  
  
     En el ejemplo siguiente se muestra texto inglés y español de botón para un comando para abrir una ventana de herramientas del explorador de árbol genealógico.  
  
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
  
## <a name="localizing-other-text-resources"></a>Localizar a otros recursos de texto  
 Recursos de texto distintos nombres de comando se definen en archivos de recursos (.resx).  
  
1.  Cambie el nombre VSPackage.resx VSPackage.en-US.resx.  
  
2.  Realizar una copia del archivo VSPackage.en-US.resx para cada idioma localizado.  
  
     Nombre de cada copia VSPackage. *Configuración regional*.resx, donde *configuración regional* es un nombre de referencia cultural determinada.  
  
3.  Cambie el nombre Resources.resx Resources.en-US.resx.  
  
4.  Realizar una copia del archivo Resources.en-US.resx para cada idioma localizado.  
  
     Nombre de cada copia de recursos. *Configuración regional*.resx, donde *configuración regional* es un nombre de referencia cultural determinada.  
  
5.  Abra cada archivo .resx para modificar los valores de cadena según corresponda para el lenguaje en particular y la referencia cultural. En el ejemplo siguiente se muestra la definición de recursos localizado de la barra de título de una ventana de herramientas.  
  
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
  
## <a name="incorporating-localized-resources-into-the-project"></a>Incorporar recursos localizados en el proyecto  
 Debe modificar el archivo assemblyinfo.cs y el archivo de proyecto para incorporar los recursos localizados.  
  
1.  Desde el **propiedades** nodo **el Explorador de soluciones**, abra el archivo assemblyinfo.cs o assemblyinfo.vb en el editor.  
  
2.  Agregue la siguiente entrada.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Esto establece el inglés de Estados Unidos como idioma predeterminado.  
  
3.  Descargar el proyecto.  
  
4.  Abra el archivo de proyecto en el editor.  
  
5.  Busque la `ItemGroup` elemento que contiene `EmbeddedResource` elementos.  
  
6.  En el `EmbeddedResource` elemento que llama VSPackage.en-US.resx, reemplace la `ManifestResourceName` elemento con un `LogicalName` elemento, que se establece en `VSPackage.en-US.Resources`, como se indica a continuación.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Para cada idioma localizado, copie el `EmbeddedResource` elemento para VsPackage.en-US y establezca el **Include** atributo y **LogicalName** elemento de la copia en la configuración regional de destino, tal y como se muestra en el siguiente ejemplo.  
  
8.  A cada uno adaptado `VSCTCompile` elemento, agregue un `ResourceName` elemento al que apunta a `Menus.ctmenu`, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Guarde el archivo de proyecto y volver a cargar el proyecto.  
  
10. Compile el proyecto.  
  
     Esto crea un ensamblado principal y los ensamblados de recursos para cada idioma. Para obtener información sobre la localización del proceso de implementación, consulte [adaptar paquetes VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Vea también  
 [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands frente a OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)