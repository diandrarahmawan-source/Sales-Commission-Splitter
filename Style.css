/* Global Reset and Base Styles */
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: 'Inter', sans-serif;
    background-color: #f7ff7f7;
    line-height: 1.5;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 1.5rem;
}

/* Header & Typography */
header {
    text-align: center;
    margin-bottom: 2rem;
}

.text-4xl { font-size: 2.25rem; }
.text-lg { font-size: 1.125rem; }
.text-xs { font-size: 0.75rem; }
.font-extrabold { font-weight: 800; }
.font-bold { font-weight: 700; }
.font-semibold { font-weight: 600; }

.text-indigo-800 { color: #3730a3; }
.text-indigo-700 { color: #4338ca; }
.text-gray-600 { color: #4b5563; }
.text-gray-400 { color: #9ca3af; }
.text-red-600 { color: #dc2626; }
.text-green-600 { color: #16a34a; }

/* Navigation (Simplified) */
.nav-container {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 2rem;
}

.nav-button {
    padding: 0.5rem 1rem;
    border-radius: 0.75rem;
    font-weight: 600;
    transition: all 150ms ease-in-out;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.06);
    cursor: pointer;
    border: 1px solid transparent;
}

.nav-button.active {
    background-color: #4f46e5;
    color: white;
}

.nav-button:not(.active) {
    background-color: white;
    color: #4f46e5;
    border-color: #4f46e5;
}

.nav-button:not(.active):hover {
    background-color: #eef2ff;
}

/* Card and Layout */
.grid-layout {
    display: grid;
    gap: 2rem;
    grid-template-columns: 1fr;
}

@media (min-width: 768px) {
    .grid-layout {
        grid-template-columns: 1fr 1fr;
    }
}

.card {
    background-color: white;
    padding: 1.5rem;
    border-radius: 0.75rem;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
    height: fit-content;
}

/* Form Styles */
.space-y-4 > * + * {
    margin-top: 1rem;
}

label {
    display: block;
    font-size: 0.875rem; /* text-sm */
    font-weight: 500;
    color: #374151; /* text-gray-700 */
    margin-bottom: 0.25rem;
}

input[type="number"],
input[type="date"],
select {
    display: block;
    width: 100%;
    padding: 0.75rem;
    border-radius: 0.5rem;
    border: 1px solid #d1d5db;
    box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
    transition: border-color 150ms, box-shadow 150ms;
}

input:focus, select:focus {
    border-color: #4f46e5;
    outline: none;
    box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.2);
}

.help-text {
    font-size: 0.75rem;
    color: #6b7280;
    margin-top: 0.25rem;
}

/* Checkbox Container */
.checkbox-container {
    padding: 0.75rem;
    border: 1px solid #d1d5db;
    border-radius: 0.5rem;
    background-color: #f9fafb;
    max-height: 10rem;
    overflow-y: auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 0.5rem;
}

.checkbox-container label {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 0.875rem;
    color: #374151;
    cursor: pointer;
    transition: color 150ms;
    margin: 0;
    font-weight: 400;
}

.checkbox-container label:hover {
    color: #4f46e5;
}

/* Buttons */
.button {
    width: 100%;
    padding: 0.75rem 1rem;
    font-weight: 700;
    border-radius: 0.75rem;
    transition: background-color 150ms, box-shadow 150ms;
    cursor: pointer;
    border: none;
}

.button-calculate {
    background-color: #10b981; /* green-500 */
    color: white;
    box-shadow: 0 10px 15px -3px rgba(16, 185, 129, 0.3), 0 4px 6px -2px rgba(16, 185, 129, 0.1);
}

.button-calculate:hover {
    background-color: #059669; /* green-700 */
}

.button.disabled {
    background-color: #d1d5db;
    cursor: not-allowed;
    box-shadow: none;
}

.button-close {
    background-color: #4f46e5;
    color: white;
}

.button-close:hover {
    background-color: #4338ca;
}

/* Table Styles */
.overflow-x-auto {
    overflow-x: auto;
}

table {
    width: 100%;
    border-collapse: collapse;
}

thead {
    background-color: #eef2ff; /* indigo-50 */
}

th {
    padding: 0.75rem 0.75rem;
    text-align: left;
    font-size: 0.75rem;
    font-weight: 600;
    color: #4f46e5;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    border-bottom: 1px solid #e5e7eb;
}

th.text-right {
    text-align: right;
}

tbody {
    background-color: white;
    border-top: 1px solid #e5e7eb;
}

td {
    padding: 0.75rem 0.75rem;
    font-size: 0.875rem;
    color: #374151;
    white-space: nowrap;
}

tbody tr:hover {
    background-color: #f9fafb;
}

td.text-right {
    text-align: right;
}

/* Utility/State Classes */
.mb-6 { margin-bottom: 1.5rem; }
.mb-4 { margin-bottom: 1rem; }
.mt-6 { margin-top: 1.5rem; }
.hidden { display: none !important; }

/* Modal Styles */
.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(75, 85, 99, 0.75); /* gray-600 with opacity */
    z-index: 50;
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal-content {
    background-color: white;
    padding: 1.5rem;
    border-radius: 0.75rem;
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
    max-width: 24rem;
    width: 100%;
    transform: scale(0.95);
    transition: transform 300ms;
}

.modal:not(.hidden) .modal-content {
    transform: scale(1);
}

