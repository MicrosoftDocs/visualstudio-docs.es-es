---
title: Localizar comandos de menú | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686133"
---
# <a name="localizing-menu-commands"></a>Adaptación de comandos de menú
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede proporcionar texto localizado para los comandos de menú y de barra de herramientas mediante la creación de archivos. Vsct localizados y archivos. resx localizados para el VSPackage y, a continuación, actualizar los archivos de proyecto para incorporar los cambios.  
  
 Para obtener información sobre cómo localizar la experiencia de instalación, consulte [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localizar nombres de comando  
 En VSPackages, los comandos de menú y los botones de barra de herramientas se definen en el archivo. Vsct.  
  
1. En **Explorador de soluciones**, cambie el nombre del archivo. Vsct de *filename*. Vsct a *filename*. en-US. Vsct.  
  
2. Haga una copia de *filename*. en-US. Vsct para cada idioma localizado.  
  
    Asigne un nombre a cada *nombre de archivo*de copia. *Locale*. Vsct, donde *configuración regional* es un nombre de referencia cultural determinado. Para obtener una lista de los valores de nombre de referencia cultural, consulte ID. de [configuración regional asignados por Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Este *nombre de archivo*. Los archivos *locale*. Vsct contendrán el texto de menú adaptado para el paquete.  
  
3. Abra cada *nombre de archivo*. El archivo *locale*. Vsct para localizar el texto.  
  
   1. Modifique los valores del elemento [ButtonText](../extensibility/buttontext-element.md) según corresponda para el idioma en cuestión.  
  
   2. Si va a proporcionar iconos localizados, modifique los valores de [mapa de bits](../extensibility/bitmap-element.md) para que apunten a los archivos de destino.  
  
      En el ejemplo siguiente se muestra el texto del botón en inglés y Español de un comando para abrir una ventana de herramientas del explorador de árbol de familia.  
  
      [FamilyTree. en-US. Vsct]  
  
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
  
    [FamilyTree.es-ES. Vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Localizar otros recursos de texto  
 Los recursos de texto que no sean nombres de comando se definen en archivos de recursos (. resx).  
  
1. Cambie el nombre de VSPackage. resx a VSPackage. en-US. resx.  
  
2. Realice una copia del archivo VSPackage. en-US. resx para cada idioma localizado.  
  
     Asigne el nombre VSPackage a cada copia. *Locale*. resx, donde *configuración regional* es un nombre de referencia cultural determinado.  
  
3. Cambie el nombre de Resources. resx a Resources. en-US. resx.  
  
4. Realice una copia del archivo resources. en-US. resx para cada idioma localizado.  
  
     Asigne a cada recurso de copia el nombre. *Locale*. resx, donde *configuración regional* es un nombre de referencia cultural determinado.  
  
5. Abra cada archivo. resx para modificar los valores de cadena según corresponda para el idioma y la referencia cultural determinados. En el ejemplo siguiente se muestra la definición de recursos adaptados para la barra de título de una ventana de herramientas.  
  
     [Resources. en-US. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Incorporar recursos localizados en el proyecto  
 Debe modificar el archivo assemblyinfo.cs y el archivo de proyecto para incorporar los recursos localizados.  
  
1. En el nodo **propiedades** de **Explorador de soluciones**, abra AssemblyInfo.cs o AssemblyInfo. VB en el editor.  
  
2. Agregue la siguiente entrada.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Esto establece el Inglés de EE. UU. como el idioma predeterminado.  
  
3. Descargue el proyecto.  
  
4. Abra el archivo de proyecto en el editor.  
  
5. Busque el `ItemGroup` elemento que contiene `EmbeddedResource` elementos.  
  
6. En el `EmbeddedResource` elemento que llama a VSPackage. en-US. resx, reemplace el `ManifestResourceName` elemento por un `LogicalName` elemento, establecido en `VSPackage.en-US.Resources` , como se indica a continuación.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Para cada idioma localizado, copie el  `EmbeddedResource` elemento para VsPackage. en-US, establezca el atributo **include** y el elemento **LogicalName** de la copia en la configuración regional de destino, tal y como se muestra en el ejemplo siguiente.  
  
8. En cada elemento localizado `VSCTCompile` , agregue un `ResourceName` elemento al que apunte `Menus.ctmenu` , tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Guarde el archivo de proyecto y vuelva a cargar el proyecto.  
  
10. Compile el proyecto.  
  
     Esto crea un ensamblado principal y ensamblados de recursos para cada idioma. Para obtener información sobre la localización del proceso de implementación, consulte [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Consulte también  
 [Extensión de menús y comandos](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands frente a OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalización y localización](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
