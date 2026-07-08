from weasyprint import HTML, CSS
from weasyprint.fonts import FontConfiguration
import os

def create_resume_pdf(html_file, css_file, output_pdf_file):
    """
    Generates a PDF resume from HTML and CSS files.

    Args:
        html_file (str): Path to the HTML resume file.
        css_file (str): Path to the CSS stylesheet.
        output_pdf_file (str): Path for the generated PDF file.
    """
    try:
        print(f"Reading HTML from: {html_file}")
        with open(html_file, 'r', encoding='utf-8') as f_html:
            html_content = f_html.read()

        print(f"Reading CSS from: {css_file}")
        with open(css_file, 'r', encoding='utf-8') as f_css:
            css_content = f_css.read()

        # Base URL is important for resolving relative paths (like images)
        base_url = os.path.dirname(os.path.abspath(html_file))
        print(f"Base URL for resolving assets: {base_url}")

        html = HTML(string=html_content, base_url=base_url)
        
        # For Font Awesome, if it's linked via CDN in HTML, WeasyPrint will try to fetch it.
        # If it's local, ensure paths are correct.
        # You can also explicitly add stylesheets:
        stylesheets = [CSS(string=css_content)]

        # Optional: If Font Awesome icons are not rendering correctly,
        # you might need to ensure WeasyPrint can find the Font Awesome font files.
        # This is more advanced and might require configuring font paths.
        # For now, let's assume the CDN link in HTML or local linking works.
        # font_config = FontConfiguration() # Default font configuration

        print(f"Generating PDF: {output_pdf_file}...")
        html.write_pdf(
            output_pdf_file,
            stylesheets=stylesheets
            # font_config=font_config # Use if you customize font loading
        )
        print(f"PDF generated successfully: {output_pdf_file}")

    except FileNotFoundError as e:
        print(f"Error: File not found - {e}")
    except Exception as e:
        print(f"An error occurred: {e}")
        import traceback
        traceback.print_exc()

if __name__ == "__main__":
    # --- Configuration ---
    html_input_file = "index.html"
    css_input_file = "style.css"
    pdf_output_file = "Avinash_Thakur_Resume.pdf"
    # -------------------

    # Ensure the script and HTML/CSS files are in the same directory,
    # or provide full paths.
    script_dir = os.path.dirname(os.path.abspath(__file__))
    html_path = os.path.join(script_dir, html_input_file)
    css_path = os.path.join(script_dir, css_input_file)
    pdf_path = os.path.join(script_dir, pdf_output_file)

    create_resume_pdf(html_path, css_path, pdf_path)
