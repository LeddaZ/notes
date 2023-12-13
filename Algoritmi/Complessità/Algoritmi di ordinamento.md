## Proprietà
- **Stabilità**: un algoritmo di ordinamento è stabile se preserva l'ordine iniziale tra due elementi con la stessa chiave (*esempio: ordinamento per nome*);
- **Ordinamento sul posto (in place)**: non crea copie dell'input per generare la sequenza ordinata;
- **Adattività**: trae vantaggio dagli elementi già ordinati.

## Selection sort
L'algoritmo seleziona di volta in volta il numero minore nella
sequenza ancora da ordinare e lo sposta nella sequenza
ordinata.

La sequenza viene quindi divisa in **due parti**: la sottosequenza
ordinata, che occupa le prime posizioni dell'array, e la
sottosequenza da ordinare, che costituisce la parte restante
dell'array su cui ri-applicare l’algoritmo.

Il selection sort scorre sempre tutta la sequenza $O(n^2)$ volte.
#### Pseudocodice
```
SelectionSort(item[] A, int n) {
	for i = 1 to n - 1 do
		int min = min(A, i, n)
		A[i] <-> A[min]
}

int min(item[] A, int i, int n) {
	for j = i + 1 to n do
		if A[j] < A[min] then
			min = j
	return min
}
```