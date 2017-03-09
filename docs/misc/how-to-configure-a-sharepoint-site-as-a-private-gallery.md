---
title: "C&#243;mo: Configurar un sitio de SharePoint como galer&#237;a privada | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint, galerías privadas"
  - "galerías privadas, Sharepoint"
ms.assetid: 6c6ed45f-7e46-4ed0-8b5c-839dbbe3769f
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# C&#243;mo: Configurar un sitio de SharePoint como galer&#237;a privada
Puede crear una página de lista de SharePoint que describa y proporcione extensiones como galería privada y agregar la lista a **Extensiones y actualizaciones**. Para obtener más información, consulta [Galerías privadas](../extensibility/private-galleries.md).  
  
 Para usar SharePoint para crear una galería privada,  
  
1.  en primer lugar, cree una página de lista para la Galería privada.  
  
2.  A continuación, cargue los archivos de extensión \(.vsix\) como elementos en la página de lista.  
  
> [!IMPORTANT]
>  Para mayor seguridad, SharePoint bloquea la carga de los archivos .vsix. Al configurar una galería privada, asegúrese de que no se bloqueen los archivos .vsix. Para obtener más información, vea [Administrar los tipos de archivos bloqueados](http://go.microsoft.com/fwlink/?LinkID=201253).  
  
## Creación de una página de lista para una galería privada  
 Los siguientes pasos pueden variar según la configuración de los servidores de SharePoint en los que se realice la implementación. En general, estas instrucciones de implementación son las mismas para cualquier extensión WSP en SharePoint. Para obtener una explicación sobre la herramienta de STSAdm, que se puede usar para administrar las implementaciones de soluciones de SharePoint, vea [Implementación de soluciones con SharePoint 2007](http://go.microsoft.com/fwlink/?LinkId=220676) en el sitio web de MSDN Magazine.  
  
#### Para crear una página de lista para una galería privada  
  
1.  Cargue el archivo de la lista de extensiones de Visual Studio \(.wsp\) en el servidor de SharePoint.  
  
2.  En un símbolo del sistema, ejecute los comandos siguientes para instalar el archivo .wsp en el servidor de SharePoint.  
  
     **stsadm –o addsolution –name VisualStudioExtensionsList.wsp**  
  
     **stsadm –o deploysolution –name VisualStudioExtensionsList.wsp –url http:\/\/\<SERVERNAME\> –allowCasPolicies –allowgacdeployment –immediate**  
  
     También tendrá que activar la característica mediante la interfaz de usuario de SharePoint para un sitio secundario, tal como se indica a continuación.  
  
    1.  En la barra de menús, elija **Acciones del sitio**, **Configuración del sitio**, **Administrar características del sitio**.  
  
    2.  Elija el botón **Activar** que hay junto a la **Biblioteca de extensiones de Visual Studio**.  
  
    3.  Agregue la biblioteca de extensión de Visual Studio para el sitio secundario que desee.  
  
 Si tiene que quitar una página de lista, siga estos pasos.  
  
#### Para quitar una página de lista para una galería privada  
  
1.  En un símbolo del sistema, ejecute los comandos siguientes para quitar el archivo .wsp en el servidor de SharePoint.  
  
     **stsadm –o retractsolution –name VisualStudioExtensionsList.wsp –immediate**  
  
     **stsadm –o deletesolution –name VisualStudioExtensionsList.wsp**  
  
2.  En SharePoint, retire y elimine la solución.  
  
## Preguntas más frecuentes  
  
### ¿Qué ocurre cuando se carga una extensión?  
 Cuando se carga un archivo de extensión \(.vsix\) de Visual Studio, la información se extrae del archivo. En primer lugar, algunos valores del archivo .vsixmanifest incrustado como, por ejemplo, VsixId, VsixVersion y así sucesivamente, se extraen y almacenan como valores de metadatos ocultos en SPListItem correspondiente. En segundo lugar, los archivos de icono y PreviewImage para la extensión se extraen y almacenan en una lista independiente.  
  
 Las imágenes se almacenan en bibliotecas de imagen denominadas *ListTitle*\_VSIXIcons y *ListTitle*\_VSIXPreviewImages, donde *ListTitle* es el nombre de la instancia de lista que almacena los archivos .vsix. Se asigna al nombre de cada archivo de imagen el identificador de VSIX correspondiente como prefijo.  
  
### ¿Qué ocurre cuando se elimina una extensión?  
 Cuando se elimina un archivo .vsix, también se eliminan los archivos de imagen correspondientes \(si existen\).  
  
### ¿Qué ocurre cuando se actualiza una extensión?  
 Una extensión se puede actualizar cargando una nueva versión del archivo .vsix y sobrescribiendo la versión existente. Cuando se actualiza una extensión, todos los valores de metadatos e imágenes para la extensión se actualizan según los valores de la nueva versión.  
  
### ¿Qué sucede cuando se elimina una lista?  
 Cuando se elimina una instancia de una lista de extensiones de Visual Studio, también se eliminan las bibliotecas de imágenes de \_VSIXPreviewImages y \_VSIXIcons correspondientes.  
  
### ¿Qué versiones de SharePoint son compatibles?  
 En la actualidad, solo SharePoint 2010 es compatible.  
  
## Vea también  
 [Galerías privadas](../extensibility/private-galleries.md)