# LicenseAuth Login Example (WinForms)

## Step 1: Install Required NuGet Package

Install the following package:

```bash
System.Runtime.Serialization.Json
```

---

## Step 2: Initialize LicenseAuth

Inside your form constructor or application startup:

```csharp
LoadInformation();
LicenseAuthApp.init();
```

---

## Step 3: Save Login Credentials

Add the following method to save the username and password locally:

```csharp
private void SaveUserAndPass()
{
    YourProjectName.Properties.Settings.Default.User = User.Text;
    YourProjectName.Properties.Settings.Default.Pass = Pass.Text;
    YourProjectName.Properties.Settings.Default.Save();
}
```

---

## Step 4: Load Saved Credentials

Add the following method to automatically load saved login information:

```csharp
private void LoadInformation()
{
    User.Text = YourProjectName.Properties.Settings.Default.User;
    Pass.Text = YourProjectName.Properties.Settings.Default.Pass;
}
```

---

## Step 5: Login Button Code

Place the following code inside your Login button click event:

```csharp
LicenseAuthApp.login(User.Text, Pass.Text);
SaveUserAndPass();

if (LicenseAuthApp.response.success)
{
    Form1 main = new Form1();
    main.Show();
    this.Hide();
}
else
{
    status.Text = LicenseAuthApp.response.message;
    Console.Beep(400, 300);
}
```

---

## Features

* User Login Authentication
* Save Username & Password
* Auto Load Saved Credentials
* LicenseAuth Integration
* Basic Login Status Handling
