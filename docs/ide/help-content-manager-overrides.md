---
title: Invalidaciones de Help Content Manager
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0610178a6249d262169abbe32f3f6a93cdd0e935
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="help-content-manager-overrides"></a>Invalidaciones de Help Content Manager

Puede modificar el comportamiento predeterminado del Visor de Ayuda y las características relacionadas con la Ayuda en el IDE de Visual Studio. Para especificar algunas opciones, es necesario crear un archivo [.pkgdef](https://blogs.msdn.microsoft.com/visualstudio/2009/12/18/whats-a-pkgdef-and-why/) con el fin de establecer diversos valores de la clave del Registro. Otros se establecen directamente en el Registro.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Cómo controlar el comportamiento del Visor de Ayuda mediante un archivo .pkgdef

1. Cree un archivo *.pkgdef* con `[$RootKey$\Help]` como primera línea.

2. Agregue en líneas independientes algunos de los valores de la clave del Registro descritos en la tabla siguiente, o todos ellos. Por ejemplo: `“UseOnlineHelp”=dword:00000001`.

3. Copie el archivo en *%Archivos de programa(x86)%\Microsoft Visual Studio\2017\\<edición\>\Common7\IDE\CommonExtensions*.

4. Ejecute `devenv /updateconfiguration` en un símbolo del sistema del desarrollador.

### <a name="registry-key-values"></a>Valores de la clave del Registro

|Valor de la clave del Registro|Tipo|Datos|Description|
|------------------|----|----|-----------|
|NewContentAndUpdateService|cadena|\<dirección URL HTTP del punto de conexión de servicio\>|Define un punto de conexión de servicio único.|
|UseOnlineHelp|dword|`0` para especificar Ayuda local, `1` para especificar Ayuda en línea|Define el valor predeterminado de la Ayuda en línea o sin conexión.|
|OnlineBaseUrl|cadena|\<dirección URL HTTP del punto de conexión de servicio\>|Define un punto de conexión F1 único.|
|OnlineHelpPreferenceDisabled|dword|`0` para habilitar o `1` para deshabilitar la opción de preferencia de Ayuda en línea|Deshabilita la opción de preferencia de Ayuda en línea.|
|DisableManageContent|dword|`0` para habilitar o `1` para deshabilitar la pestaña **Administrar contenido** en el Visor de Ayuda|Deshabilite la pestaña **Administrar contenido**|
|DisableFirstRunHelpSelection|dword|`0` para habilitar o `1` para deshabilitar las características de ayuda que se configuran la primera vez que se inicia Visual Studio.|Deshabilita la instalación de contenido en el primer inicio de Visual Studio.|

### <a name="example-pkgdef-file-contents"></a>Contenido del archivo .pkgdef de ejemplo

```
[$RootKey$\Help]
“NewContentAndUpdateService”=”https://some.service.endpoint”
“UseOnlineHelp”=dword:00000001
“OnlineBaseUrl”=”https://some.service.endpoint”
“OnlineHelpPreferenceDisabled”=dword:00000000
“DisableManageContent”=dword:00000000
“DisableFirstRunHelpSelection”=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Uso del Editor del Registro para cambiar el comportamiento del Visor de Ayuda

Los dos comportamientos siguientes pueden controlarse mediante el establecimiento de valores de la clave del Registro en el Editor del Registro.

|Tarea|Clave del Registro|Valor|Datos|
|----------|-----|------|----|
|Invalidar la prioridad de trabajos del servicio BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (en un equipo de 64 bits)\Microsoft\Help\v2.3|BITSPriority|**foreground**, **high**, **normal** o **low**|
|Apuntar al almacén de contenido local en un recurso compartido de red|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Vea también

- [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md)
- [Argumentos de línea de comandos para Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md)
- [Visor de Ayuda de Microsoft](../ide/microsoft-help-viewer.md)
- [Modificación del Shell aislado mediante el archivo .pkgdef](../extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)