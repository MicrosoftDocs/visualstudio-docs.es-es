---
title: "C&#243;mo: Actualizar plantillas existentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plantillas de elementos, actualizar las plantillas existentes"
  - "plantillas de proyecto, actualizar las plantillas existentes"
  - "plantillas de Visual Studio, actualizar las plantillas existentes"
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Actualizar plantillas existentes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Después de crear una plantilla y comprimir los archivos en un archivo .zip, es posible que desee modificarla.  Puede hacerlo al cambiar los archivos de la misma de forma manual o al exportar una nueva plantilla de un proyecto basado en la plantilla.  
  
## Utilizar el Asistente para exportar plantillas para actualizar una plantilla existente  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona un **Asistente para exportar plantillas** que se puede utilizar para actualizar una plantilla existente.  
  
#### Para usar Exportar plantilla para actualizar una plantilla existente  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, en **Nuevo proyecto**.  
  
2.  Seleccione la plantilla que desee actualizar, especifique un nombre y una ubicación para el proyecto temporal y haga clic en **Aceptar**.  
  
3.  Modifique el proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  En el menú **Archivo**, haga clic en **Exportar plantilla** y use el asistente **Exportar plantilla** para crear una nueva plantilla.  
  
5.  Una vez comprimida la plantilla actualizada en un archivo .zip, elimine el archivo .zip de plantilla anterior.  
  
## Actualizar manualmente una plantilla existente  
 Puede actualizar una plantilla existente fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si modifica los archivos del archivo .zip comprimido.  
  
#### Para actualizar manualmente una plantilla existente  
  
1.  Busque el archivo .zip que contiene la plantilla.  De forma predeterminada, este archivo se encuentra en \\Mis documentos\\Visual Studio *versión*\\My Exported Templates\\.  
  
2.  Extraiga el archivo .zip.  
  
3.  Modifique o elimine los archivos de plantilla actuales, o agregue nuevos archivos a la plantilla.  
  
4.  Abra, modifique y guarde el archivo XML .vstemplate para controlar el comportamiento actualizado o los nuevos archivos.  Para obtener más información sobre el esquema .vstemplate, vea [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  Para obtener más información sobre lo que se puede parametrizar en los archivos de origen, consulte [Parámetros de plantilla](../ide/template-parameters.md)  
  
5.  Seleccione los archivos de la plantilla, haga clic con el botón secundario, haga clic en **Enviar a** y, a continuación, en **Carpetas comprimidas \(en zip\)**.  Los archivos seleccionados se comprimen en un archivo .zip.  
  
6.  Coloque el nuevo archivo .zip en el mismo directorio que el antiguo.  
  
7.  Elimine los archivos de plantilla extraídos y el archivo .zip de plantilla antiguo.  
  
8.  Inicie \(como administrador\) una instancia del símbolo del sistema para desarrolladores \(en el menú Inicio, en **Visual Studio 2010 \/ Visual Studio Tools\/Símbolo del sistema para desarrolladores**\).  
  
9. Ejecute el comando siguiente: `devenv /installvstemplates`.  
  
## Vea también  
 [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Cómo: Crear Starter Kits](../ide/how-to-create-starter-kits.md)