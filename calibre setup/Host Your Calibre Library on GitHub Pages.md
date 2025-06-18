### 📦 Step 1: Export Your Library to HTML

1. Open **Calibre**
    
2. Top menu → **Convert books** → **Create a catalog**
    
3. Choose:
    
    - **Format**: `HTML`
        
    - Select fields you want included (authors, series, tags, etc.)
        
4. Calibre will generate a folder like:
    
    bash
    
    CopyEdit
    
    `calibre-library/index.html calibre-library/images/ calibre-library/styles/`
    

---

### 🌐 Step 2: Set Up a GitHub Repo

1. Go to [https://github.com](https://github.com)
    
2. Click **"New Repository"**
    
    - Name it something like `calibre-library`
        
    - Set it to **Public** (or Private if using GitHub Pro + Pages)
        
3. **Do NOT initialize with a README**
    

---

### 🧠 Step 3: Upload Your Calibre HTML Files

**Option A: Drag & Drop**

1. Open your new repo
    
2. Click **"Add file" → "Upload files"**
    
3. Drag your entire `calibre-library` folder contents into the browser (not the folder itself—its contents)
    
4. Click **"Commit changes"**
    

**Option B: Git (for power users)**

bash

CopyEdit

`git clone https://github.com/yourusername/calibre-library.git cd calibre-library cp -r /path/to/your/exported/catalog/* . git add . git commit -m "Initial commit" git push origin main`

---

### 🚀 Step 4: Enable GitHub Pages

1. Go to your repo’s **Settings → Pages**
    
2. Under **"Source"**, choose:
    
    - **Branch**: `main`
        
    - **Folder**: `/ (root)`
        
3. Click **Save**
    

GitHub will give you a public link like:

arduino

CopyEdit

`https://yourusername.github.io/calibre-library/`

---

### 🧪 Step 5: Test It!

Visit the link. You should see your clickable HTML catalog, styled and browsable!

---

Want help making the HTML layout prettier or including download links to the actual EPUBs or PDFs? I can walk you through that too.