from playwright.sync_api import sync_playwright

seeds = range(25, 35)
total = 0

with sync_playwright() as p:
    browser = p.chromium.launch(headless=True)
    page = browser.new_page()

    for seed in seeds:
        url = f"https://sanand0.github.io/tdsdata/js_table/?seed={seed}"
        print("Processing", url)

        page.goto(url, timeout=60000)
        page.wait_for_selector("td")

        cells = page.query_selector_all("td")

        for cell in cells:
            text = cell.inner_text().strip()
            if text.replace("-", "").isdigit():
                total += int(text)

    browser.close()

print("FINAL TOTAL:", total)
