---
title: Localización de comandos de menú ? Microsoft Docs
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702943"
---
# <a name="localize-menu-commands"></a>Localizar comandos de menú

Puede proporcionar texto localizado para los comandos de menú y barra de herramientas mediante la creación de archivos *.vsct* localizados y archivos *.resx localizados* para el VSPackage y, a continuación, actualizar los archivos de proyecto para incorporar los cambios.

Para obtener información sobre cómo localizar la experiencia de instalación, consulte [Localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localizar nombres de comandos

En VSPackages, los comandos de menú y los botones de barra de herramientas se definen en el archivo *.vsct.*

1. En el **Explorador**de soluciones , cambie el nombre del archivo *.vsct* de *filename.vsct* a *filename.en-US.vsct*.

2. Haga una copia de *filename.en-US.vsct* para cada idioma localizado.

    Asigne un nombre a cada nombre de *archivo de copia. Locale .vsct*, donde *.locale* es un nombre de referencia cultural determinado. Para obtener una lista de valores de nombre de referencia cultural, vea Valores de configuración regional [asignados por Microsoft](/windows/uwp/publish/supported-languages).

    Estos *nombre de archivo. Los archivos Locale.vsct* contendrán el texto del menú localizado del paquete.

3. Abra cada *nombre de archivo. Locale.vsct* para localizar el texto.

   1. Modifique los valores del elemento [ButtonText](../extensibility/buttontext-element.md) según corresponda para el idioma determinado.

   2. Si va a proporcionar iconos localizados, modifique los valores de [mapa](../extensibility/bitmap-element.md) de bits para que apunten a los archivos de destino.

      En el ejemplo siguiente se muestra el texto de los botones en inglés y español de un comando para abrir una ventana de herramientas del Explorador de árboles genealógicos.

      [*FamilyTree.en-US.vsct*]

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

    [*FamilyTree.es-ES.vsct*]

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

## <a name="localize-other-text-resources"></a>Localizar otros recursos de texto

Los recursos de texto distintos de los nombres de comando se definen en archivos de recursos (*.resx*).

1. Cambie el nombre de *VSPackage.resx* a *VSPackage.en-US.resx*.

2. Haga una copia del archivo *VSPackage.en-US.resx* para cada idioma localizado.

     Asigne un nombre a cada copia *de VSPackage. Locale .resx*, donde *.Locale* es un nombre de referencia cultural determinado.

3. Cambie el nombre de *Resources.resx* a *Resources.en-US.resx*.

4. Haga una copia del archivo *Resources.en-US.resx* para cada idioma localizado.

     Asigne un nombre a cada copia *de Recursos. Locale .resx*, donde *.Locale* es un nombre de referencia cultural determinado.

5. Abra cada archivo *.resx* para modificar los valores de cadena según corresponda para el idioma y la referencia cultural concretos. En el ejemplo siguiente se muestra la definición de recursos localizados para la barra de título de una ventana de herramientas.

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

Debe modificar el archivo *de assemblyinfo.cs* y el archivo de proyecto para incorporar los recursos localizados.

1. Desde el nodo **Propiedades** del Explorador de **soluciones**, abra *assemblyinfo.cs* o *assemblyinfo.vb* en el editor.

2. Agregue la siguiente entrada.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Esto establece el inglés de EE. UU. como idioma predeterminado.

3. Descargue el proyecto.

4. Abra el archivo de proyecto en el editor.

5. En el `Project` elemento raíz, agregue un `PropertyGroup` elemento con un `UICulture` elemento que coincida con el idioma predeterminado.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Esto establece el inglés de EE. UU. como la referencia cultural de interfaz de usuario predeterminada para los controles de Windows Presentation Foundation (WPF).

6. Busque `ItemGroup` el elemento `EmbeddedResource` que contiene elementos.

7. En `EmbeddedResource` el elemento que llama a *VSPackage.en-US.resx*, reemplace el `ManifestResourceName` elemento por un `LogicalName` elemento establecido en , como se indica a `VSPackage.en-US.Resources`continuación:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Para cada idioma localizado, `EmbeddedResource` `VsPackage.en-US`copie el elemento para , y establezca el atributo **Include** y el elemento **LogicalName** de la copia en la configuración regional de destino.

9. A cada `VSCTCompile` elemento localizado, agregue `ResourceName` `Menus.ctmenu`un elemento que apunte a , como se muestra en el ejemplo siguiente:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Guarde el archivo de proyecto y vuelva a cargar el proyecto.

11. Compile el proyecto.

     Esto crea un ensamblado principal y ensamblados de recursos para cada idioma. Para obtener información sobre cómo localizar el proceso de implementación, consulte [Localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Vea también

- [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
