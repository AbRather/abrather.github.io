# Reference Letters Feature - Setup & Usage Guide

## ✅ Implementation Complete

The reference letters feature has been successfully implemented across your portfolio website. This guide will help you set up and manage your reference letter PDFs.

---

## 📁 Directory Structure

```
/static/pdf/references/
  ├── README.md
  ├── studentische_hilfskraft.pdf
  ├── werkstudent_flight_demonstrator.pdf
  ├── propulsion_test_data_intern.pdf
  ├── propulsion_design_intern.pdf (optional - currently marked as unavailable)
  └── werkstudent_advanced_computational.pdf
```

---

## 🎯 Features Implemented

### 1. **Reference Badge Icons**
- Gold certificate icon (🏅) appears next to job titles that have references
- Hover effect with animation and tooltip
- Only shows if reference is marked as `available: true`

### 2. **Modal Popup**
- Professional modal window opens when badge is clicked
- Displays PDF inline using iframe
- Smooth loading animation
- Error handling for missing PDFs

### 3. **PDF Viewer**
- Full-screen PDF viewer in modal
- Download button
- Open in new tab button
- Responsive design for mobile devices

### 4. **Error Handling**
- Checks if PDF exists before loading
- Shows friendly error message if PDF is missing
- Disables download/open buttons if file doesn't exist
- No console errors - graceful degradation

---

## 📝 File Naming Convention

### Current Configuration (in `_data/careers.yml`):

| Position | PDF Filename | Status |
|----------|-------------|--------|
| Faserinstitut Bremen | `studentische_hilfskraft.pdf` | ✅ Available |
| Polaris Spaceplanes | `werkstudent_flight_demonstrator.pdf` | ✅ Available |
| Rocket Factory Augsburg | `propulsion_test_data_intern.pdf` | ✅ Available |
| SpanTrik | `propulsion_design_intern.pdf` | ❌ Not Available |
| SRM Institute | `werkstudent_advanced_computational.pdf` | ✅ Available |

---

## 🚀 How to Add/Update Reference Letters

### Step 1: Prepare Your PDF
1. Scan or export your reference letter as PDF
2. Optimize for web (compress if needed - keep under 2MB)
3. Name it according to the convention above

### Step 2: Upload PDF
Place the PDF file in:
```
/static/pdf/references/[filename].pdf
```

### Step 3: Update careers.yml (if needed)
If adding a new position, add the reference section:

```yaml
- name:
    detail: Your Job Title @ Company
    i18n: job_key
  desc:
    details:
      - Job description point 1
      - Job description point 2
    i18n: job_des
  date:
    detail: Month Year - Month Year
    i18n: job_date
  job:
    detail: Position Title
    i18n: job_title
  icon: fa-icon-name
  reference:
    available: true  # Set to false if no reference yet
    filename: your_filename.pdf
    title: Reference Letter - Company Name
```

### Step 4: Test
1. Build your Jekyll site locally: `jekyll serve`
2. Navigate to the Career section
3. Look for the gold badge icon next to the job title
4. Click to open the modal
5. Verify PDF loads correctly

---

## 🔧 Enabling/Disabling References

### To Hide a Reference (if you don't have the PDF yet):
In `_data/careers.yml`, change:
```yaml
reference:
  available: false  # Change to false
  filename: propulsion_design_intern.pdf
  title: Reference Letter - SpanTrik
```

### To Show a Reference:
Change `available: false` to `available: true` and ensure the PDF file exists.

---

## 🎨 Customization Options

### Change Badge Icon
In `/static/css/custom-career.css`, find:
```css
.reference-badge i {
    color: #f9aa43;  /* Change color */
    font-size: 18px;  /* Change size */
}
```

### Change Modal Colors
In `/static/css/custom-career.css`, find:
```css
.reference-modal .modal-header {
    background: linear-gradient(135deg, #046b99 0%, #00a6d2 100%);
}
```

---

## 🐛 Troubleshooting

### Badge not appearing?
- Check `available: true` in careers.yml
- Verify the reference section exists for that career entry
- Clear browser cache and reload

### PDF not loading?
- Verify PDF filename matches exactly (case-sensitive)
- Check PDF is in `/static/pdf/references/` directory
- Ensure PDF is not corrupted
- Check file size (should be under 5MB)

### Modal not opening?
- Check browser console for JavaScript errors
- Ensure jQuery and Bootstrap are loaded
- Clear browser cache

### Mobile display issues?
- The design is responsive and should work on all devices
- If issues persist, check viewport meta tag in head

---

## 📱 Mobile Behavior

- Badge icon scaled appropriately for touch targets
- Modal is full-width on mobile
- PDF viewer height adjusted for smaller screens
- Download button available for offline viewing
- Tooltip disabled on very small screens

---

## 🔒 Security Notes

- PDFs are served statically from your GitHub Pages
- No sensitive data should be embedded in filenames
- Consider watermarking PDFs if privacy is a concern
- PDFs are publicly accessible once uploaded

---

## ✨ Testing Checklist

Before deploying to production:

- [ ] All PDF files are in the correct directory
- [ ] Filenames match exactly in careers.yml
- [ ] PDFs are optimized for web (compressed)
- [ ] Test on desktop browser
- [ ] Test on mobile device
- [ ] Test modal open/close functionality
- [ ] Test download button
- [ ] Test "open in new tab" button
- [ ] Verify error handling for missing PDFs
- [ ] Check hover animations work smoothly
- [ ] Verify badge appears only where expected

---

## 📊 Files Modified

1. **_data/careers.yml** - Added reference data structure
2. **_includes/sections/career.html** - Added badge icons and modals
3. **static/css/custom-career.css** - Added styling for badges and modals
4. **static/pdf/references/** - Created directory for PDFs

---

## 🎓 Example: Adding a New Reference

Let's say you get a new reference letter for your SpanTrik position:

1. **Save the PDF as:** `propulsion_design_intern.pdf`
2. **Upload to:** `/static/pdf/references/propulsion_design_intern.pdf`
3. **Update careers.yml:**
   ```yaml
   reference:
     available: true  # Changed from false
     filename: propulsion_design_intern.pdf
     title: Reference Letter - SpanTrik
   ```
4. **Commit and push** to GitHub
5. **Wait for GitHub Pages** to rebuild (usually 1-2 minutes)
6. **Test** the live site

---

## 💡 Best Practices

1. **File Naming:** Use lowercase, underscores, and descriptive names
2. **File Size:** Keep PDFs under 2MB for faster loading
3. **Quality:** Use at least 150 DPI for scanned documents
4. **Format:** Ensure PDFs are properly formatted (portrait orientation)
5. **Privacy:** Remove sensitive information before uploading
6. **Backups:** Keep original copies in a secure location
7. **Updates:** If you get updated references, keep old filenames consistent

---

## 🆘 Support

If you encounter issues:
1. Check browser console for errors (F12 → Console)
2. Verify file paths are correct
3. Test in different browsers
4. Check Jekyll build logs for errors
5. Review this guide's troubleshooting section

---

## 📈 Future Enhancements (Optional)

Consider these potential improvements:
- Add reference letter preview thumbnails
- Implement PDF page navigation
- Add print functionality
- Create an admin panel for easy management
- Add reference letter validity dates
- Implement access logging

---

**Last Updated:** November 15, 2025
**Version:** 1.0
**Status:** ✅ Production Ready
