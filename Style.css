// --- Data Mockup (Sales List) ---
const SALES_LIST = [
    { id: 1, name: "Diandra" },
    { id: 2, name: "Miftah" },
    { id: 3, name: "Dewan" },
    { id: 4, name: "Arman" },
    { id: 5, name: "Kusnandar" },
    { id: 6, name: "Gunawan" },
    { id: 7, name: "Nury" },
    { id: 8, name: "Anto" },
    { id: 9, name: "Dewi" }
];

const COMMISSION_RATES = {
    LEAD_GEN: 0.25,
    TELEMARKETING: 0.25,
    CONVERSION: 0.50,
    COMBINED: 0.75 // 25% + 50%
};

let latestCommissionDetails = [];

// --- Utility Functions ---

/**
 * Mengubah angka menjadi format Rupiah (Rp).
 * @param {number} number
 * @returns {string}
 */
function formatRupiah(number) {
    if (number === undefined || number === null || isNaN(number)) return 'Rp 0';
    const cleanNumber = Math.round(number);
    // Menggunakan Intl.NumberFormat Indonesia (IDR)
    return new Intl.NumberFormat('id-ID', {
        style: 'currency',
        currency: 'IDR',
        minimumFractionDigits: 0,
        maximumFractionDigits: 0
    }).format(cleanNumber);
}

/**
 * Menampilkan modal pesan kustom.
 * @param {string} title
 * @param {string} body
 */
function showModal(title, body) {
    document.getElementById('modal-title').textContent = title;
    document.getElementById('modal-body').textContent = body;
    document.getElementById('message-modal').classList.remove('hidden');
}

// --- Core Calculation Logic ---

/**
 * Menghitung pembagian komisi berdasarkan logika bisnis.
 * @param {number} price - Harga Properti
 * @param {string[]} leadGens - Array nama Lead Generator
 * @param {string} telemarketing - Nama staf Telemarketing
 * @param {string} conversion - Nama staf Lead Conversion
 * @returns {Object[]} - Detail pembagian komisi
 */
function calculateSplit(price, leadGens, telemarketing, conversion) {
    const total = price;
    const results = [];
    const leadgensCount = leadGens.length;
    
    // 1. Lead Generator Share (25% split equally)
    if (leadgensCount > 0) {
        const leadgenPool = total * COMMISSION_RATES.LEAD_GEN;
        // Gunakan Math.round untuk pembulatan Rupiah terdekat
        const leadgenShare = Math.round(leadgenPool / leadgensCount);
        const leadgenPercentage = (COMMISSION_RATES.LEAD_GEN / leadgensCount) * 100;

        leadGens.forEach(name => {
            const salesPerson = SALES_LIST.find(s => s.name === name);
            results.push({
                sales_id: salesPerson.id,
                name: name,
                role: 'Lead Generator',
                percentage: leadgenPercentage,
                amount: leadgenShare
            });
        });
    }

    const isCombined = telemarketing === conversion;

    // 2. Telemarketing Share (25%) and Conversion Share (50%)
    if (isCombined) {
        // Combined Role (Telemarketing + Conversion = 75%)
        const combinedShare = Math.round(total * COMMISSION_RATES.COMBINED);
        const salesPerson = SALES_LIST.find(s => s.name === telemarketing);
        results.push({
            sales_id: salesPerson.id,
            name: telemarketing,
            role: 'Telemarketing & Conversion',
            percentage: COMMISSION_RATES.COMBINED * 100,
            amount: combinedShare
        });
    } else {
        // Separate Roles
        const teleShare = Math.round(total * COMMISSION_RATES.LEAD_GEN); // 25%
        const convShare = Math.round(total * COMMISSION_RATES.CONVERSION); // 50%

        // Telemarketing (25%)
        const telePerson = SALES_LIST.find(s => s.name === telemarketing);
        results.push({
            sales_id: telePerson.id,
            name: telemarketing,
            role: 'Telemarketing',
            percentage: COMMISSION_RATES.LEAD_GEN * 100,
            amount: teleShare
        });

        // Conversion (50%)
        const convPerson = SALES_LIST.find(s => s.name === conversion);
        results.push({
            sales_id: convPerson.id,
            name: conversion,
            role: 'Lead Conversion',
            percentage: COMMISSION_RATES.CONVERSION * 100,
            amount: convShare
        });
    }

    return results;
}

// --- DOM Manipulation and Event Handlers ---

function populateSalesDropdowns() {
    const telemarketingEl = document.getElementById('telemarketing');
    const conversionEl = document.getElementById('conversion');
    const leadgensContainer = document.getElementById('leadgens-checkbox-container');

    const salesOptions = SALES_LIST.map(s => `<option value="${s.name}">${s.name}</option>`).join('');
    
    // Populate Dropdowns
    telemarketingEl.innerHTML += salesOptions;
    conversionEl.innerHTML += salesOptions;

    // Populate Checkboxes
    leadgensContainer.innerHTML = SALES_LIST.map(s => `
        <label>
            <input type="checkbox" name="leadgen_name" value="${s.name}">
            <span>${s.name}</span>
        </label>
    `).join('');
}

function handleCalculate() {
    const priceEl = document.getElementById('price');
    const telemarketingEl = document.getElementById('telemarketing');
    const conversionEl = document.getElementById('conversion');
    const leadgensContainer = document.getElementById('leadgens-checkbox-container');

    const price = parseFloat(priceEl.value);
    const selectedLeadGens = Array.from(leadgensContainer.querySelectorAll('input[name="leadgen_name"]:checked')).map(input => input.value);
    const telemarketing = telemarketingEl.value;
    const conversion = conversionEl.value;

    // --- Validation ---
    if (!price || price <= 0) {
        showModal("Kesalahan Input", "Harga Properti harus diisi dengan angka yang valid.");
        return;
    }
    if (selectedLeadGens.length === 0) {
        showModal("Kesalahan Input", "Minimal harus memilih satu Lead Generator.");
        return;
    }
    if (!telemarketing || !conversion) {
        showModal("Kesalahan Input", "Semua peran (Telemarketing dan Conversion) harus dipilih.");
        return;
    }
    // --- End Validation ---

    latestCommissionDetails = calculateSplit(price, selectedLeadGens, telemarketing, conversion);

    // Display Results
    const totalCommission = latestCommissionDetails.reduce((sum, item) => sum + item.amount, 0);
    
    document.getElementById('output-price').textContent = formatRupiah(price);
    document.getElementById('output-total-commission').textContent = formatRupiah(totalCommission);

    const tableBody = document.getElementById('commission-table-body');
    tableBody.innerHTML = ''; // Clear previous results
    
    latestCommissionDetails.forEach(detail => {
        const row = tableBody.insertRow();
        row.className = 'hover:bg-gray-50';
        
        const nameCell = row.insertCell();
        nameCell.textContent = detail.name;
        
        const roleCell = row.insertCell();
        roleCell.textContent = detail.role;
        
        const percentageCell = row.insertCell();
        percentageCell.textContent = `${detail.percentage.toFixed(2)}%`;
        percentageCell.classList.add('text-right');
        
        const nominalCell = row.insertCell();
        nominalCell.textContent = formatRupiah(detail.amount);
        nominalCell.classList.add('text-right', 'font-bold', 'text-indigo-600');
    });

    // Show result card
    document.getElementById('result-card').classList.remove('hidden');
}

function setupEventListeners() {
    // Set default date to today
    document.getElementById('date').value = new Date().toISOString().split('T')[0];

    // Calculate Button
    document.getElementById('calculate-btn').addEventListener('click', handleCalculate);

    // Modal Close Button
    document.getElementById('modal-close-btn').addEventListener('click', () => {
        document.getElementById('message-modal').classList.add('hidden');
    });

    // Checkbox Max Limit Logic
    const leadgensContainer = document.getElementById('leadgens-checkbox-container');
    const helpText = document.getElementById('leadgen-help-text');

    leadgensContainer.addEventListener('change', (event) => {
        if (event.target.type === 'checkbox') {
            const checkedCount = leadgensContainer.querySelectorAll('input[name="leadgen_name"]:checked').length;
            
            if (checkedCount > 10) {
                event.target.checked = false; // Uncheck the box that caused the overflow
                showModal("Batas Maksimum", "Maksimal hanya 10 Lead Generator yang dapat dipilih.");
            }
            
            // Update helper text style
            if (checkedCount >= 10) {
                helpText.textContent = "Batas maksimal 10 Lead Generator telah tercapai.";
                helpText.style.color = '#dc2626'; /* text-red-600 */
            } else {
                helpText.textContent = "Ceklis nama staf yang terlibat. (Maksimal 10).";
                helpText.style.color = '#6b7280'; /* text-gray-500 */
            }
        }
    });
}

// Initialization on window load
window.onload = function() {
    populateSalesDropdowns();
    setupEventListeners();
};

