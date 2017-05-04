---
title: "Debe habilitar expl&#237;citamente el acceso al sistema del proyecto de Microsoft Office Visual Basic para Aplicaciones antes de crear o abrir un proyecto en Visual Studio Tools para Microsoft Office System | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vst.project.vbawrongversion"
  - "VST.Project.VBASecurityGenericError"
  - "VST.Project.VBASecurityPermissions"
  - "VST.SelectDocWizard.MissingCOM"
  - "VST.Project.VBASecurityNotSet"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 538021e6-1776-453d-9899-d7fca2f1f58f
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Debe habilitar expl&#237;citamente el acceso al sistema del proyecto de Microsoft Office Visual Basic para Aplicaciones antes de crear o abrir un proyecto en Visual Studio Tools para Microsoft Office System
  Los proyectos de desarrollo de Office requieren acceso al sistema de proyectos de Visual Basic para Aplicaciones en Microsoft Office Word y Microsoft Office Excel, aunque los proyectos no usen Visual Basic para aplicaciones.  La compatibilidad con controles en tiempo de diseño en proyectos de Visual Basic y C\# depende del sistema de proyectos de Visual Basic para Aplicaciones.  
  
 Algunos virus de macro de Microsoft Office intentan automatizar el sistema de proyectos de Visual Basic para Aplicaciones a fin de propagarse.  Al habilitar el acceso al sistema de proyectos de Visual Basic para Aplicaciones, se quita una protección que ayuda a impedir la propagación de los virus de macro.  No obstante, la seguridad de macros normal sigue aplicándose, con lo que el nivel de seguridad de macros y la lista de editores de confianza que mantiene para las aplicaciones de Office determinarán si se ejecuta una macro en el equipo.  
  
> [!NOTE]  
>  Esto solo es válido para el equipo de desarrollo.  No es necesario que esta opción esté habilitada en los equipos de los usuarios finales para poder ejecutar soluciones de Office.  
  
 Es importante señalar que la mera deshabilitación del acceso al sistema de proyectos de Visual Basic para Aplicaciones no le protege frente a los virus, sino que simplemente ayuda a impedir la propagación de algunos virus a otros documentos si el equipo se infecta con un virus de macro.  La opción está deshabilitada de manera predeterminada como capa de protección adicional para el equipo, pero si la habilita, su equipo no será más susceptible a virus si sigue los procedimientos recomendados de seguridad.  
  
 La mejor protección contra los virus de macro de Office es ejecutar Office en el nivel de seguridad Alto o Muy alto, confiar solo en macros de orígenes verificados y conocidos, y estar al día con las revisiones de seguridad y los antivirus.  
  
 Para más información sobre la protección de su PC frente a virus y otro código malintencionado, vea [http:\/\/www.microsoft.com\/protect](http://www.microsoft.com/protect).  
  
 Puede habilitar o deshabilitar manualmente la opción **Confiar en el acceso a proyectos de Visual Basic**.  
  
 Puede reparar la instalación de Office si ve errores de VBA o COM.  
  
### Para habilitar o deshabilitar el acceso a proyectos de Visual Basic  
  
1.  En el menú **Herramientas** de Word o Excel, elija **Macro** y después haga clic en **Seguridad**.  
  
2.  En el cuadro de diálogo **Seguridad**, haga clic en la pestaña **Editores de confianza**.  
  
3.  Active o desactive **Confiar en el acceso a proyectos de Visual Basic**.  
  
4.  Haga clic en **Aceptar**.  
  
### Para establecer el nivel de seguridad de las macros de Office  
  
1.  En el menú **Herramientas** de Word o Excel, elija **Macro** y después haga clic en **Seguridad**.  
  
2.  En la pestaña **Nivel de seguridad**, seleccione la configuración deseada.  
  
     La pestaña **Nivel de seguridad** contiene detalles sobre cada nivel.  Para obtener más información, vea el tema sobre los niveles de seguridad de macros en la Ayuda de Office.  
  
### Para instalar VBA con 2007 Microsoft Office system  
  
1.  En el Panel de control, ejecute **Agregar o quitar programas** o **Programas y características**.  
  
2.  Seleccione Office en la lista **Programas actualmente instalados**.  
  
3.  Haga clic en **Cambiar**.  
  
4.  Seleccione **Agregar o quitar funciones** y, a continuación, haga clic en **Continuar**.  
  
5.  Seleccione **Elegir personalización avanzada de aplicaciones** y luego haga clic en **Siguiente**.  
  
6.  Expanda **Características compartidas de Office** en la lista **Elija las opciones de actualización para aplicaciones y herramientas**.  
  
7.  Abra el menú desplegable junto a **Visual Basic para Aplicaciones** y, a continuación, haga clic en **Ejecutar desde mi PC**.  
  
8.  Haga clic en **Continuar**.  
  
9. Haga clic en **Cerrar**.  
  
### Para reparar la instalación de Office  
  
1.  En el Panel de control, ejecute **Agregar o quitar programas** o **Programas y características**.  
  
2.  Seleccione la versión de Office en la lista **Programas actualmente instalados**.  
  
3.  Haga clic en **Cambiar**.  
  
4.  Seleccione **Reinstalar o reparar** y, a continuación, haga clic en **Siguiente**.  
  
5.  Seleccione **Detectar y reparar errores en la instalación de Office** y, a continuación, haga clic en **Instalar**.  
  
## Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)  
  
  