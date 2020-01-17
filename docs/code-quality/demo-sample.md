---
title: Proyecto de ejemplo de C++ para el análisis de código
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 84f6ddc2012617a5216c58fa0761dc100fb8942f
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75402741"
---
# <a name="sample-c-project-for-code-analysis"></a>Proyecto de ejemplo de C++ para el análisis de código

El procedimiento siguiente muestra cómo crear el ejemplo de [Tutorial: Analizar código de C/C++ en busca de defectos](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). El procedimiento crea:

- Una solución [! INCLUDEvsprvs] denominada CppDemo.

- Un proyecto de biblioteca estática denominado CodeDefects.

- Un proyecto de biblioteca estática denominado Annotations.

Los procedimientos también proporcionan el código para el encabezado y los archivos *.cpp* para las bibliotecas estáticas.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Crear la solución CppDemo y el proyecto CodeDefects

1. Abra [!INCLUDEvsprvs] y seleccione **Crear un nuevo proyecto**.

2. Cambie el filtro de lenguaje a **C++** .

3. Seleccione **Proyecto vacío** y haga clic en **Siguiente**.

4. En el cuadro de texto **Nombre de proyecto**, escriba **CodeDefects**.

5. En el cuadro de texto **Nombre de la solución**, escriba **CppDemo**.

6. Haga clic en **Crear**

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurar el proyecto CodeDefects como una biblioteca estática

1. En Explorador de soluciones, haga clic con el botón derecho en **CodeDefects** y luego haga clic en **Propiedades**.

2. Expanda **Propiedades de configuración** y haga clic en **General**.

3. En la lista **General**, cambie **Tipo de configuración** por **Biblioteca estática (.lib)** .

4. En la lista **Opciones avanzadas**, cambie **Extensión de nombre de archivo** a **.lib**.

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Agregar el archivo de encabezado y código fuente al proyecto CodeDefects

1. En Explorador de soluciones, expanda **CodeDefects**, haga clic con el botón derecho en **Archivos de encabezado**, haga clic en **Agregar** y luego en **Nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Código** y luego en **Archivo de encabezado (.h)** .

3. En el cuadro **Nombre**, escriba **Bug.h** y haga clic en **Agregar**.

4. Copie el código siguiente y péguelo en el archivo *Bug.h* en el editor.

```cpp
#pragma once

#include <windows.h>

// These functions are consumed by the sample
// but are not defined. This project cannot be linked!
bool CheckDomain(LPCTSTR);
HRESULT ReadUserAccount();

// These constants define the common sizes of the
// user account information throughout the program
const int USER_ACCOUNT_LEN = 256;
const int ACCOUNT_DOMAIN_LEN = 128;
```

5. En Explorador de soluciones, haga clic con el botón derecho en **Archivos de código fuente**, seleccione **Nuevo** y haga clic en **Nuevo elemento**.

6. En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Archivo C++ (.cpp)** .

7. En el cuadro **Nombre**, escriba **Bug.cpp** y haga clic en **Agregar**.

8. Copie el código siguiente y péguelo en el archivo *Bug.cpp* en el editor.

```cpp
#include "Bug.h"

// the user account
TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
int len = 0;

bool ProcessDomain()
{
    TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
    // ReadUserAccount gets a 'domain\user' input from
    //the user into the global 'g_userAccount'
    if (ReadUserAccount())
    {
        // Copies part of the string prior to the '\'
        // character onto the 'domain' buffer
        for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
        {
            if (g_userAccount[len] == '\\')
            {
                // Stops copying on the domain and user separator ('\')
                break;
            }
            domain[len] = g_userAccount[len];
        }
        if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
        {
            // '\' was not found. Invalid domain\user string.
            delete[] domain;
            return false;
        }
        else
        {
            domain[len] = '\0';
        }
        // Process domain string
        bool result = CheckDomain(domain);

        delete[] domain;
        return result;
    }
    return false;
}

int path_dependent(int n)
{
    int i;
    int j;
    if (n == 0)
        i = 1;
    else
        j = 1;
    return i + j;
}
```

9. Haga clic en el menú **Archivo** y luego en **Guardar todo**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Agregar el proyecto Annotations y configurarlo como una biblioteca estática

1. En Explorador de soluciones, haga clic en **CppDemo**, seleccione **Agregar** y haga clic en **Nuevo proyecto**.

2. En el cuadro de diálogo **Agregar un nuevo proyecto**, cambie el filtro de lenguaje a **C++** y seleccione **Proyecto vacío**; a continuación, haga clic en **Siguiente**.

3. En el cuadro de texto **Nombre de proyecto**, escriba **Anotaciones** y haga clic en **Crear**.

4. En Explorador de soluciones, haga clic con el botón derecho en **Annotations** y luego haga clic en **Propiedades**.

5. Expanda **Propiedades de configuración** y haga clic en **General**.

6. En la lista **General**, cambie a **Tipo de configuración** y, a continuación, haga clic en **Biblioteca estática (.lib)** .

7. En la lista **Avanzado**, seleccione el texto de la columna situada junto a **Extensión de archivo de destino** y, después, escriba **.lib**.


## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Agregar el archivo de encabezado y código fuente al proyecto Annotations

1. En Explorador de soluciones, expanda **Annotations**, haga clic con el botón derecho en **Archivos de encabezado**, haga clic en **Agregar** y luego en **Nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Archivo de encabezado (.h)** .

3. En el cuadro **Nombre**, escriba **annotations.h** y haga clic en **Agregar**.

4. Copie el código siguiente y péguelo en el archivo *annotations.h* en el editor.

```cpp
#pragma once
#include <sal.h>

struct LinkedList
{
    struct LinkedList* next;
    int data;
};

typedef struct LinkedList LinkedList;

_Ret_maybenull_ LinkedList* AllocateNode();
```

5. En Explorador de soluciones, haga clic con el botón derecho en **Archivos de código fuente**, seleccione **Nuevo** y haga clic en **Nuevo elemento**.

6. En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Código** y luego en **Archivo C++ (.cpp)** .

7. En el cuadro **Nombre**, escriba **annotations.cpp** y haga clic en **Agregar**.

8. Copie el código siguiente y péguelo en el archivo *annotations.cpp* en el editor.

```cpp
#include "annotations.h"

LinkedList* AddTail(LinkedList* node, int value)
{
    // finds the last node
    while (node->next != nullptr)
    {
        node = node->next;
    }

    // appends the new node
    LinkedList* newNode = AllocateNode();
    newNode->data = value;
    newNode->next = 0;
    node->next = newNode;

    return newNode;
}
```

9. Haga clic en el menú **Archivo** y luego en **Guardar todo**.


La solución ya está completa y debe compilarse sin errores.
