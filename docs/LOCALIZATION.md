# Japanese Localization

This document describes the Japanese localization implementation for Textream.

## Implementation Details

### Localization Files

The application supports two languages:
- **English (en)**: Base language - `Textream/en.lproj/Localizable.strings`
- **Japanese (ja)**: Japanese translation - `Textream/ja.lproj/Localizable.strings`

### How It Works

1. **LocalizationHelper.swift**: Provides a convenient `.localized` extension on String for easy localization
2. **Localizable.strings**: Contains key-value pairs for all UI strings in both languages
3. **Dynamic Language Selection**: macOS automatically selects the appropriate language based on the system language settings

### Switching Languages

To test the Japanese localization:

1. Open System Settings
2. Go to General → Language & Region
3. Add Japanese (日本語) to preferred languages
4. Restart the Textream app

The app will automatically display in Japanese if it's set as the preferred language.

### Coverage

All UI elements have been localized:
- Menu items (File, Edit, Help menus)
- Main window UI (buttons, labels, placeholders)
- Settings dialog (all tabs and options)
- Alert dialogs (errors, confirmations, updates)
- About window
- Tooltips and descriptions

## For Developers

### Adding New Strings

When adding new UI strings:

1. Add the string key and English text to `en.lproj/Localizable.strings`
2. Add the corresponding Japanese translation to `ja.lproj/Localizable.strings`
3. Use the string in code with `.localized`:

```swift
Text("my_key".localized)
```

For strings with parameters:

```swift
Text("my_key".localized(param1, param2))
```

### String Format Guidelines

- Use descriptive keys in snake_case: `update_available`, `failed_to_save_file`
- Keep translations contextually appropriate
- Maintain formatting (newlines, punctuation) between languages
- Test with actual data to ensure proper display
