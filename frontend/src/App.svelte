<!-- src/routes/+page.svelte -->
<script lang="ts">
    import { Input } from "$lib/components/ui/input";
    import { Button } from "$lib/components/ui/button";
    import {
        Table,
        TableBody,
        TableCell,
        TableHead,
        TableHeader,
        TableRow,
    } from "$lib/components/ui/table";
    import { Loader2 } from "lucide-svelte";

    let linkedInUrl = "";
    let sessionCookie = "";
    let isLoading = false;
    let error: string | null = null;

    interface Company {
        company_name: string; // Changed to match API
        location: string;
        employees_count: number; // Changed to match API
        sales_url: string;
        public_url: string;
    }

    let companies: Company[] = [];

    async function handleSubmit() {
        if (!linkedInUrl || !sessionCookie) {
            error = "Please fill in both fields";
            return;
        }

        error = null;
        isLoading = true;

        try {
            // or : http://localhost:8080/api/scrape || https://bam-api.bamen.dev/api/scrape
            const response = await fetch("http://localhost:8080/api/scrape", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                    "X-API-Token": "token1234",
                },
                body: JSON.stringify({
                    url: linkedInUrl,
                    sessionCookie: sessionCookie,
                }),
            });

            if (!response.ok) {
                const errorData = await response.json();
                throw new Error(errorData.error || "Failed to fetch data");
            }

            const data = await response.json();
            companies = data.data; // Access the data array from the response
        } catch (err) {
            error = err instanceof Error ? err.message : "An error occurred";
        } finally {
            isLoading = false;
        }
    }
</script>

<div class="container mx-auto space-y-6 p-4">
    <!-- Header -->
    <h1 class="text-2xl font-bold">LinkedIn Sales Navigator Scraper</h1>
    <form
        on:submit|preventDefault={handleSubmit}
        class="flex items-center gap-4"
    >
        <div class="flex-1">
            <Input
                type="text"
                placeholder="LinkedIn Sales Navigator URL"
                bind:value={linkedInUrl}
                disabled={isLoading}
            />
        </div>

        <div class="flex-1">
            <Input
                type="text"
                placeholder="Session Cookie"
                bind:value={sessionCookie}
                disabled={isLoading}
            />
        </div>

        <Button type="submit" disabled={isLoading}>
            {#if isLoading}
                <Loader2 class="mr-2 h-4 w-4 animate-spin" />
                Scraping...
            {:else}
                Start Scraping
            {/if}
        </Button>
    </form>

    {#if error}
        <p class="text-sm text-red-500">{error}</p>
    {/if}

    {#if companies.length > 0}
        <div class="rounded-md border">
            <Table>
                <TableHeader>
                    <TableRow>
                        <TableHead>Company Name</TableHead>
                        <TableHead>Type</TableHead>
                        <TableHead>Employees</TableHead>
                        <TableHead>Actions</TableHead>
                    </TableRow>
                </TableHeader>
                <TableBody>
                    {#each companies as company}
                        <TableRow>
                            <TableCell>{company.company_name}</TableCell>
                            <TableCell>
                                {company.location.split("\n")[0].trim()}
                                <!-- Take only the first line -->
                            </TableCell>
                            <TableCell>{company.employees_count}</TableCell>
                            <TableCell>
                                <div class="flex gap-2">
                                    <a
                                        href={company.public_url}
                                        target="_blank"
                                        rel="noopener noreferrer"
                                        class="text-blue-500 hover:underline"
                                    >
                                        Public Profile
                                    </a>
                                    <a
                                        href={company.sales_url}
                                        target="_blank"
                                        rel="noopener noreferrer"
                                        class="text-blue-500 hover:underline"
                                    >
                                        Sales Profile
                                    </a>
                                </div>
                            </TableCell>
                        </TableRow>
                    {/each}
                </TableBody>
            </Table>
        </div>
    {:else if !isLoading}
        <p class="text-center text-gray-500">
            No data available. Start scraping to see results.
        </p>
    {/if}
</div>
