---
title: "Avoid too many blank lines"
tags: ["AL","Readability"]
categories: ["Best Practice"]
---

## Description

Avoid too many blank lines.

## Example 1

### Bad code

```al
var
    UserSetup: Record "User Setup";
    IsEditable: Boolean;
    IsVisible: Boolean;


local procedure Initialize()
begin
    IsEditable := false;
    IsVisible := false;


    UserSetup.Get();
end;
```

### Good code

```al
var
    UserSetup: Record "User Setup";
    IsEditable: Boolean;
    IsVisible: Boolean;

local procedure Initialize()
begin
    IsEditable := false;
    IsVisible := false;

    UserSetup.Get();
end;
```

## Example 2

### Bad code

```al
page 50000 "Blank Lines"
{
    PageType = List;
    ApplicationArea = All;
    UsageCategory = Administration;
    SourceTable = Customer;


    layout
    {
        area(Content)
        {
            repeater(GroupName)
            {
                ShowCaption = false;


                field(Name; Rec.Name)
                {
                    ApplicationArea = All;
                }
            }
        }
    }
}
```

### Good code

```al
page 50000 "Blank Lines"
{
    PageType = List;
    ApplicationArea = All;
    UsageCategory = Administration;
    SourceTable = Customer;

    layout
    {
        area(Content)
        {
            repeater(GroupName)
            {
                ShowCaption = false;

                field(Name; Rec.Name)
                {
                    ApplicationArea = All;
                }
            }
        }
    }
}
```

## Example 3

### Bad code

```al
var
    GLSetup: Record "General Ledger Setup";
    GLSetupRead: Boolean;


local procedure GetGLSetup()
begin
    if not GLSetupRead then
        GLSetup.Get();


    GLSetupRead := true;


    OnAfterGetGLSetup(GLSetup);
end;


[IntegrationEvent(false, false)]
local procedure OnAfterGetGLSetup(var GLSetup: Record "General Ledger Setup")
begin
end;
```

### Good code

```al
var
    GLSetup: Record "General Ledger Setup";
    GLSetupRead: Boolean;

local procedure GetGLSetup()
begin
    if not GLSetupRead then
        GLSetup.Get();

    GLSetupRead := true;

    OnAfterGetGLSetup(GLSetup);
end;

[IntegrationEvent(false, false)]
local procedure OnAfterGetGLSetup(var GLSetup: Record "General Ledger Setup")
begin
end;
```

## Tips

The [AZ AL Dev Tools/AL Code Outline](https://marketplace.visualstudio.com/items?itemName=andrzejzwierzchowski.al-code-outline) extension adds two new commands to Visual Studio Code to remove empty duplicate lines.

- `Remove Empty Lines from the Active Editor` : removes empty duplicate lines from the current editor
- `Remove Empty Lines from the Active Project` : removes empty duplicate lines from the current project