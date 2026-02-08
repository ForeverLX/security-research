# DOM-Based XSS via Image Source Attribute

## 🎯 Objective

Trigger DOM-based XSS from within an HTML attribute without breaking out of the attribute context.

## 🔍 Vulnerability Analysis

- **Type**: DOM-Based Cross-Site Scripting (XSS)
- **Target**: Image gallery application
- **Parameter**: `art` parameter controlling image source
- **Flaw**: User input placed directly into `src` attribute without encoding
- **Impact**: JavaScript execution via event handlers

## 💥 Exploitation

**Initial Attempt**: Traditional tag breaking failed due to URL encoding

**Successful Payload**:
test.jpg" onerror="alert(document.domain)

text

**How It Works**:

1. `test.jpg` - Provides valid filename base
2. `"` - Closes existing `src` attribute
3. `onerror="alert(document.domain)"` - Adds malicious event handler
4. Broken image URL triggers `onerror` event

**Result**: Image load failure triggers JavaScript execution

## 🛡️ Mitigation Strategies

1. **DOM Sanitization**: Sanitize all DOM modifications
2. **Safe DOM APIs**: Use `textContent` instead of `innerHTML`
3. **Input Validation**: Validate and encode before DOM insertion
4. **Content Security Policy**: Restrict inline script execution

## 📊 Skills Demonstrated

- **DOM Manipulation**: Understanding client-side rendering vulnerabilities
- **Event Handler Exploitation**: Using legitimate events for malicious purposes
- **Context Preservation**: Working within attribute context without breaking out

_Conducted in controlled environment for educational purposes. All sensitive information (IPs, credentials, session tokens) has been sanitized for security._
