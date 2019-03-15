---
title: Habilitar el acceso a VBA para crear o abrir un proyecto de Visual Studio Tools para el proyecto de Microsoft Office system
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10dc439946cb209c9a8d8e0c5ff50a7e8cfe5363
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869323"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Habilitar el acceso a VBA para crear o abrir un proyecto de Visual Studio Tools para el proyecto de Microsoft Office system

Debe habilitar explícitamente acceso a Visual Basic para el sistema de proyectos de aplicaciones (VBA) en Microsoft Office antes de que puede crear o abrir un proyecto de Visual Studio Tools para el proyecto de Microsoft Office system.

 Proyectos de desarrollo de Microsoft Office requieren acceso a Visual Basic para el sistema de proyectos de aplicaciones (VBA) en Microsoft Office Word y Microsoft Office Excel, aunque los proyectos no usen Visual Basic para aplicaciones. La compatibilidad con controles en tiempo de diseño en proyectos de Visual Basic y C# depende del sistema de proyectos de Visual Basic para Aplicaciones.

 Algunos virus de macro de Microsoft Office intentan automatizar el sistema de proyectos de Visual Basic para Aplicaciones a fin de propagarse. Al habilitar el acceso al sistema de proyectos de Visual Basic para Aplicaciones, se quita una protección que ayuda a impedir la propagación de los virus de macro. No obstante, la seguridad de macros normal sigue aplicándose, con lo que el nivel de seguridad de macros y la lista de editores de confianza que mantiene para las aplicaciones de Office determinarán si se ejecuta una macro en el equipo.

> [!NOTE]
> Esto solo es válido para el equipo de desarrollo. Equipos de usuario final no necesitan esta opción habilitada para ejecutar soluciones de Office.

 Es importante señalar que la mera deshabilitación del acceso al sistema de proyectos de Visual Basic para Aplicaciones no le protege frente a los virus, sino que simplemente ayuda a impedir la propagación de algunos virus a otros documentos si el equipo se infecta con un virus de macro. La opción está deshabilitada de manera predeterminada como capa de protección adicional para el equipo, pero si la habilita, su equipo no será más susceptible a virus si sigue los procedimientos recomendados de seguridad.

 La mejor protección contra virus de macro es ejecutar Office en el nivel de seguridad alto o muy alto, confiar únicamente en las macros de orígenes verificados y conocidos, de Office y mantenerse al día con las revisiones de seguridad y antivirus.

 Puede habilitar o deshabilitar la opción **confiar en el acceso al proyecto de Visual Basic** manualmente.

 Puede reparar la instalación de Office si ve errores de VBA o COM.

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Para habilitar o deshabilitar el acceso a proyectos de Visual Basic

1. Haga clic en la pestaña **Archivo** .

2. Haga clic en **Opciones**.

3. Haga clic en **centro de confianza**y, a continuación, haga clic en **configuración del centro de confianza**.

4. En el **centro de confianza**, haga clic en **configuración de la Macro**.

5. Active o desactive **confiar en el acceso al modelo de objetos del proyecto VBA** para habilitar o deshabilitar el acceso a proyectos de Visual Basic.

6. Haga clic en **Aceptar**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Para habilitar o deshabilitar el acceso a proyectos de Visual Basic con 2007 Microsoft Office system

1. En el **herramientas** menú en Word o Excel, apunte a **Macro**y, a continuación, haga clic en **seguridad**.

2. En el **seguridad** cuadro de diálogo, haga clic en el **editores de confianza** ficha.

3. Seleccione para habilitar o desactive para deshabilitar, **confiar en el acceso al proyecto de Visual Basic**.

4. Haga clic en **Aceptar**.

## <a name="to-set-your-office-macro-security-level"></a>Para establecer el nivel de seguridad de las macros de Office

1. Haga clic en la pestaña **Archivo** .

2. Haga clic en **Opciones**.

3. Haga clic en **centro de confianza**y, a continuación, haga clic en **configuración del centro de confianza**.

4. En el **centro de confianza**, haga clic en **configuración de la Macro**.

5. En el **configuración de la Macro** , seleccione la opción que desee.

6. Haga clic en **Aceptar**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Para establecer el nivel de seguridad de macros de Office con 2007 Microsoft Office system

1. En el **herramientas** menú en Word o Excel, apunte a **Macro**y, a continuación, haga clic en **seguridad**.

2. En el **nivel de seguridad** pestaña, seleccione la opción que desee.

    El **nivel de seguridad** pestaña contiene detalles sobre cada nivel. Para obtener más información, vea el tema sobre los niveles de seguridad de macros en la Ayuda de Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Para instalar VBA con 2007 Microsoft Office system

1. En el Panel de Control, ejecute **agregar o quitar programas** o **programas y características**.

2. Seleccione Office en el **programas actualmente instalados** lista.

3. Haga clic en **cambio**.

4. Seleccione **agregar o quitar funciones**y, a continuación, haga clic en **continuar**.

5. Seleccione **Elegir personalización avanzada de aplicaciones**y, a continuación, haga clic en **siguiente**.

6. Expanda **características compartidas de Office** en el **elija las opciones de actualización de aplicaciones y herramientas** lista.

7. Abra el menú desplegable junto a **Visual Basic para aplicaciones**y, a continuación, haga clic en **ejecutar desde Mi PC**.

8. Haga clic en **Continuar**.

9. Haga clic en **Cerrar**.

## <a name="to-repair-your-installation-of-office"></a>Para reparar la instalación de Office

1. En el Panel de Control, ejecute **agregar o quitar programas** o **programas y características**.

2. Seleccione la versión de Office en el **programas actualmente instalados** lista.

3. Haga clic en **cambio**.

4. Seleccione **reinstalar o reparar**y, a continuación, haga clic en **siguiente**.

5. Seleccione **detectar y reparar errores en la instalación de Office**y, a continuación, haga clic en **instalar**.

## <a name="see-also"></a>Vea también
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)