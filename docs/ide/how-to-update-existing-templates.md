---
title: "Cómo: Actualizar plantillas existentes | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 28ae63c6dba9d352025d5c87d838772a81cf989d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-existing-templates"></a>Cómo: Actualizar plantillas existentes
Después de crear una plantilla y comprimir los archivos en un archivo .zip, es posible que desee modificarla. Puede hacerlo al cambiar los archivos de la misma de forma manual o al exportar una nueva plantilla de un proyecto basado en la plantilla.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Usar el Asistente para exportar plantillas para actualizar una plantilla existente  
Visual Studio proporciona un **Asistente para exportar plantillas** que se puede usar para actualizar una plantilla existente.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Para usar Exportar plantilla para actualizar una plantilla existente  
  
1.  Abra el cuadro de diálogo **Nuevo proyecto**; para ello, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  Seleccione la plantilla que quiera actualizar, escriba un nombre y una ubicación para el proyecto y elija **Aceptar**.  
  
3.  Modifique el proyecto en Visual Studio.  
  
4.  En el menú **Proyecto**, elija **Exportar plantilla**.  

    Se abre el **Asistente para exportar plantillas**.  

5.  Siga las indicaciones del asistente para exportar la plantilla como un archivo .zip.  

6.  Elimine el archivo .zip de la plantilla antigua.  
  
## <a name="manually-updating-an-existing-template"></a>Actualizar manualmente una plantilla existente  
Puede actualizar una plantilla existente fuera de Visual Studio si modifica los archivos del archivo .zip comprimido.  
  
#### <a name="to-manually-update-an-existing-template"></a>Para actualizar manualmente una plantilla existente  
  
1.  Busque el archivo .zip que contiene la plantilla. De forma predeterminada, este archivo se encuentra en %USERPROFILE%\Documentos\Visual Studio \<versión\>\My Exported Templates\..  
  
2.  Extraiga el archivo .zip.  
  
3.  Modifique o elimine los archivos de plantilla actuales, o agregue nuevos archivos a la plantilla.  
  
4.  Abra, modifique y guarde el archivo XML .vstemplate para controlar el comportamiento actualizado o los nuevos archivos.  

    Para obtener más información sobre el esquema .vstemplate, vea [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md) (Referencia de esquema de plantillas de Visual Studio). Para más información sobre lo que se puede parametrizar en los archivos de origen, vea [Parámetros de plantilla](../ide/template-parameters.md).  
  
5.  Seleccione los archivos de la plantilla, haga clic con el botón derecho, elija **Enviar a** y después **Carpeta comprimida (en zip)**.  

    Los archivos seleccionados se comprimen en un archivo .zip.  
  
6.  Coloque el nuevo archivo .zip en el mismo directorio que el antiguo.  
  
7.  Elimine los archivos de plantilla extraídos y el archivo .zip de plantilla antiguo.  
  
8.  Inicie una instancia con privilegios elevados del símbolo del sistema para desarrolladores:  

  1. En el menú Inicio, vaya a **Visual Studio \<versión\>**, **Símbolo del sistema para desarrolladores**.  

  2. En el menú contextual (clic con el botón derecho), elija **Más**, **Ejecutar como administrador**.  
  
9. Ejecute el comando siguiente: `devenv /installvstemplates`.  
  
## <a name="see-also"></a>Vea también  
[Personalizar plantillas](../ide/customizing-project-and-item-templates.md)   
[Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
[Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
[Parámetros de plantilla](../ide/template-parameters.md)   
[Cómo: Crear Starter Kits](../ide/how-to-create-starter-kits.md)