---
title: "Item cannot be added to the Toolbox. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_NOTSUPPORTEDDATA"
  - "vs.message.0x800A0065"
ms.assetid: 69fa5e73-bbc6-462c-95ca-bf2ee32d43ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Item cannot be added to the Toolbox.
Este error se suele producir al intentar agregar un elemento para el que el Cuadro de herramientas no puede mostrar un icono de acceso directo.  
  
 Entre los elementos que muestra el Cuadro de herramientas se incluyen:  
  
-   Controles y componentes de .NET Framework instalados en el equipo local.  
  
 **Nota** Para que los controles y componentes de los formularios Web Forms de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se muestren en el Cuadro de herramientas, deben contar con una propiedad [AspNetHostingPermission.Level Property](https://msdn.microsoft.com/en-us/library/system.web.aspnethostingpermission.level.aspx) establecida en "Unlimited".  
  
-   Texto seleccionado arrastrado o pegado desde un editor de Visual Studio, como los fragmentos de código.  
  
 Entre los elementos que no muestra el Cuadro de herramientas se incluyen:  
  
-   Archivos de libro de Excel.  
  
-   Ensamblados de .NET Framework instalados en servidores de red compartidos.  
  
    > [!NOTE]
    >  Los ensamblados agregados desde una ruta UNC no son de plena confianza, por lo que no obtienen los permisos necesarios para aparecer en el Cuadro de herramientas.  
  
### Para corregir este error  
  
1.  Utilice el cuadro de diálogo **Personalizar cuadro de herramientas** para agregar un control o componente instalado en el equipo local a la ficha activa del Cuadro de herramientas.  
  
     \-O bien\-  
  
2.  Arrastre o pegue el texto seleccionado en un editor de Visual Studio en el Cuadro de herramientas.  
  
## Vea también  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/es-es/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/es-es/21285050-cadd-455a-b1f5-a2289a89c4db)   
 [cuadro de herramientas](../ide/reference/toolbox.md)