---
title: Acceso VBA para crear o abrir un proyecto de sistema de VSTO
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
titleSuffix: Visual Studio Tools for Microsoft Office
ms.custom: seodec18
ms.date: 08/14/2019
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
ms.openlocfilehash: 3199b23f7ad1bb45fd509d2a9b5cd21da1a49971
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551545"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Habilitar el acceso a VBA para crear o abrir un Visual Studio Tools para el proyecto de sistema de Microsoft Office

Debe habilitar explícitamente el acceso al sistema de proyectos de Visual Basic para Aplicaciones (VBA) en Microsoft Office para poder crear o abrir un Visual Studio Tools para el proyecto de sistema de Microsoft Office.

 Los proyectos de desarrollo de Microsoft Office requieren acceso al sistema de proyectos de Visual Basic para Aplicaciones (VBA) en Microsoft Office Word y Microsoft Office Excel, aunque los proyectos no utilicen Visual Basic para Aplicaciones. La compatibilidad con controles en tiempo de diseño en proyectos de Visual Basic y C# depende del sistema de proyectos de Visual Basic para Aplicaciones.

 Algunos virus de macro de Microsoft Office intentan automatizar el sistema de proyectos de Visual Basic para Aplicaciones a fin de propagarse. Al habilitar el acceso al sistema de proyectos de Visual Basic para Aplicaciones, se quita una protección que ayuda a impedir la propagación de los virus de macro. No obstante, la seguridad de macros normal sigue aplicándose, con lo que el nivel de seguridad de macros y la lista de editores de confianza que mantiene para las aplicaciones de Office determinarán si se ejecuta una macro en el equipo.

> [!NOTE]
> Esto solo es válido para el equipo de desarrollo. Los equipos de los usuarios finales no necesitan esta opción habilitada para ejecutar soluciones de Office.

 Es importante señalar que la mera deshabilitación del acceso al sistema de proyectos de Visual Basic para Aplicaciones no le protege frente a los virus, sino que simplemente ayuda a impedir la propagación de algunos virus a otros documentos si el equipo se infecta con un virus de macro. La opción está deshabilitada de manera predeterminada como capa de protección adicional para el equipo, pero si la habilita, su equipo no será más susceptible a virus si sigue los procedimientos recomendados de seguridad.

 La mejor protección contra los virus de macros de Office es ejecutar Office en el nivel de seguridad alto o muy alto, para confiar solo en las macros de orígenes de datos comprobados y conocidos, y para mantenerse al día con las revisiones de seguridad y los detectores de virus.

 Puede habilitar o deshabilitar la opción **confiar en el acceso a Visual Basic proyecto** manualmente.

 Puede reparar la instalación de Office si ve errores de VBA o COM.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Para habilitar o deshabilitar el acceso a proyectos de Visual Basic

1. Haga clic en la pestaña **Archivo** .

2. Haga clic en **Opciones**.

3. Haga clic en **centro de confianza**y, a continuación, en configuración del **centro de confianza**.

4. En el **centro de confianza**, haga clic en **configuración de macro**.

5. Active o desactive **el acceso de confianza al modelo de objetos de proyecto de VBA** para habilitar o deshabilitar el acceso a proyectos de Visual Basic.

6. Haga clic en **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Para habilitar o deshabilitar el acceso a Visual Basic proyectos con el sistema Microsoft Office 2007

1. En el menú **herramientas** de Word o Excel, elija **macro**y, a continuación, haga clic en **seguridad**.

2. En el cuadro de diálogo **seguridad** , haga clic en la pestaña **editores de confianza** .

3. Seleccione esta casilla para habilitar o deshabilitar el **acceso de confianza a Visual Basic proyecto**.

4. Haga clic en **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Para establecer el nivel de seguridad de las macros de Office

1. Haga clic en la pestaña **Archivo** .

2. Haga clic en **Opciones**.

3. Haga clic en **centro de confianza**y, a continuación, en configuración del **centro de confianza**.

4. En el **centro de confianza**, haga clic en **configuración de macro**.

5. En la sección **configuración de macro** , seleccione el valor deseado.

6. Haga clic en **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Para establecer el nivel de seguridad de macros de Office con el sistema Microsoft Office 2007

1. En el menú **herramientas** de Word o Excel, elija **macro**y, a continuación, haga clic en **seguridad**.

2. En la pestaña **nivel de seguridad** , seleccione el valor que desee.

    La pestaña **nivel de seguridad** contiene detalles sobre cada nivel. Para obtener más información, vea el tema sobre los niveles de seguridad de macros en la Ayuda de Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Para instalar VBA con 2007 Microsoft Office system

1. En el panel de control, ejecute **Agregar o quitar programas** o **programas y características**.

2. Seleccione Office en la lista **programas actualmente instalados** .

3. Haga clic en **cambiar**.

4. Seleccione **Agregar o quitar características**y, a continuación, haga clic en **continuar**.

5. Seleccione **elegir personalización avanzada de aplicaciones**y, a continuación, haga clic en **siguiente**.

6. Expanda Características compartidas de **Office** en la lista **Elija las opciones de actualización para aplicaciones y herramientas** .

7. Abra el menú desplegable situado junto a **Visual Basic para aplicaciones**y, a continuación, haga clic en **Ejecutar desde mi PC**.

8. Haga clic en **Continuar**.

9. Haga clic en **Cerrar**.

## <a name="to-repair-your-installation-of-office"></a>Para reparar la instalación de Office

1. En el panel de control, ejecute **Agregar o quitar programas** o **programas y características**.

2. Seleccione su versión de Office en la lista **programas actualmente instalados** .

3. Haga clic en **cambiar**.

4. Seleccione **reinstalar o reparar**y, a continuación, haga clic en **siguiente**.

5. Seleccione **detectar y reparar errores en la instalación de Office**y, a continuación, haga clic en **instalar**.

## <a name="see-also"></a>Vea también
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
