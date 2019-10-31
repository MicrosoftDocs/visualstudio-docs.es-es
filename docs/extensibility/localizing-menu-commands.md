---
title: Localizar comandos de menú | Microsoft Docs
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94f71014440c55da0151d0ebd817aac9f5d2c7ed
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186279"
---
# <a name="localize-menu-commands"></a>Localizar comandos de menú

Puede proporcionar texto localizado para los comandos de menú y de barra de herramientas mediante la creación de archivos *. Vsct* localizados y archivos *. resx* localizados para el VSPackage y, a continuación, actualizar los archivos de proyecto para incorporar los cambios.

Para obtener información sobre cómo localizar la experiencia de instalación, vea [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Localizar nombres de comando

En VSPackages, los comandos de menú y los botones de barra de herramientas se definen en el archivo *. Vsct* .

1. En **Explorador de soluciones**, cambie el nombre del archivo *. Vsct* de *filename. Vsct* a *filename. en-US. Vsct*.

2. Haga una copia de *filename. en-US. Vsct* para cada idioma localizado.

    Nombre cada nombre de archivo de copia *. { Locale}. Vsct*, donde *{locale}* es un nombre de referencia cultural determinado. Para obtener una lista de los valores de nombre de referencia cultural, consulte ID. de [configuración regional asignados por Microsoft](/windows/uwp/publish/supported-languages).

    Este *nombre de archivo. Los archivos locale. Vsct* contendrán el texto de menú adaptado para el paquete.

3. Abra cada *nombre de archivo. El archivo locale. Vsct* para localizar el texto.

   1. Modifique los valores del elemento [ButtonText](../extensibility/buttontext-element.md) según corresponda para el idioma en cuestión.

   2. Si va a proporcionar iconos localizados, modifique los valores de [mapa de bits](../extensibility/bitmap-element.md) para que apunten a los archivos de destino.

      En el ejemplo siguiente se muestra el texto del botón en inglés y Español de un comando para abrir una ventana de herramientas del explorador de árbol de familia.

      [*Familytree. en-US. Vsct*]

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

    [*Familytree.es-es. Vsct*]

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

Los recursos de texto que no sean nombres de comando se definen en archivos de recursos ( *. resx*).

1. Cambie el nombre de *VSPackage. resx* a *VSPackage. en-US. resx*.

2. Realice una copia del archivo *VSPackage. en-US. resx* para cada idioma localizado.

     Asigne un nombre a cada VSPackage de copia *. { Locale}. resx*, donde *{locale}* es un nombre de referencia cultural determinado.

3. Cambie el nombre de *Resources. resx* a *Resources. en-US. resx*.

4. Realice una copia del archivo *Resources. en-US. resx* para cada idioma localizado.

     Asigne un nombre a cada recurso de copia *. { Locale}. resx*, donde *{locale}* es un nombre de referencia cultural determinado.

5. Abra cada archivo *. resx* para modificar los valores de cadena según corresponda para el idioma y la referencia cultural determinados. En el ejemplo siguiente se muestra la definición de recursos adaptados para la barra de título de una ventana de herramientas.

     [*Resources. en-US. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-es. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporar recursos localizados en el proyecto

Debe modificar el archivo *AssemblyInfo.CS* y el archivo de proyecto para incorporar los recursos localizados.

1. En el nodo **propiedades** de **Explorador de soluciones**, Abra *AssemblyInfo.CS* o *AssemblyInfo. VB* en el editor.

2. Agregue la siguiente entrada.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Esto establece el Inglés de EE. UU. como el idioma predeterminado.

3. Descargue el proyecto.

4. Abra el archivo de proyecto en el editor.

5. En el elemento `Project` raíz, agregue un elemento `PropertyGroup` con un elemento `UICulture` que coincida con el idioma predeterminado.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Esto establece el Inglés de EE. UU. como la referencia cultural predeterminada de la interfaz de usuario para los controles de Windows Presentation Foundation (WPF).

6. Busque el elemento `ItemGroup` que contiene `EmbeddedResource` elementos.

7. En el elemento `EmbeddedResource` que llama a *VSPackage. en-US. resx*, reemplace el elemento `ManifestResourceName` por un elemento `LogicalName` que esté establecido en `VSPackage.en-US.Resources`, como se indica a continuación:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Para cada idioma localizado, copie el elemento `EmbeddedResource` de `VsPackage.en-US`y establezca el atributo **include** y el elemento **LogicalName** de la copia en la configuración regional de destino.

9. Agregue un elemento `ResourceName` que apunte a `Menus.ctmenu`, tal y como se muestra en el ejemplo siguiente, a cada elemento `VSCTCompile` localizado:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Guarde el archivo de proyecto y vuelva a cargar el proyecto.

11. Compile el proyecto.

     Esto crea un ensamblado principal y ensamblados de recursos para cada idioma. Para obtener información sobre la localización del proceso de implementación, consulte [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Vea también

- [Extender menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
