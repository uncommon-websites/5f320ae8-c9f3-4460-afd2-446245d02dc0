<!--
@component Pricing

Please update features according to the company's product offering. Do not remove this comment.
-->
<script lang="ts">
	// Types
	type PricingTier = {
		name: string;
		monthlyPrice?: number | null;
		yearlyPrice?: number | null;
		description: string;
		features: string[];
		cta: {
			label: string;
			href: string;
		};
		highlight?: boolean;
	};

	type PricingFeature = {
		name: string;
		tiers: {
			[key: string]: boolean | string;
		};
	};

	// Components
	import Button from "$lib/components/ui/Button.svelte";
	import SectionHeader from "./SectionHeader.svelte";
	import IconCheck from "~icons/lucide/check";
	import IconX from "~icons/lucide/x";
	import NumberFlow from "@number-flow/svelte";
	import LogoScroller from "./LogoScroller.svelte";

	// Props
	const {
		title = "Creative AI, built for creative control",
		subtitle = "Plans for every kind of creative",
		tierNames = ["Free", "Pro", "Agency", "Enterprise"],
		features = [
			{
				name: "Projects",
				tiers: {
					Free: "3",
					Pro: "Unlimited",
					Agency: "Unlimited",
					Enterprise: "Unlimited"
				}
			},
			{
				name: "AI credits/month",
				tiers: {
					Free: "20",
					Pro: "200",
					Agency: "2,500",
					Enterprise: "Custom"
				}
			},
			{
				name: "Seats",
				tiers: {
					Free: "1",
					Pro: "1",
					Agency: "10",
					Enterprise: "Flexible"
				}
			},
			{
				name: "Team workspaces",
				tiers: {
					Free: false,
					Pro: false,
					Agency: true,
					Enterprise: true
				}
			},
			{
				name: "Shared assets/libraries",
				tiers: {
					Free: false,
					Pro: false,
					Agency: true,
					Enterprise: true
				}
			},
			{
				name: "Creative AI models (text, image, video)",
				tiers: {
					Free: true,
					Pro: true,
					Agency: true,
					Enterprise: true
				}
			},
			{
				name: "Export options (image, video, layers)",
				tiers: {
					Free: false,
					Pro: true,
					Agency: true,
					Enterprise: true
				}
			},
			{
				name: "Custom styles",
				tiers: {
					Free: false,
					Pro: "1 active",
					Agency: "Multiple",
					Enterprise: "2+ libraries"
				}
			},
			{
				name: "Priority/support SLA",
				tiers: {
					Free: "Email, standard",
					Pro: "Priority email",
					Agency: "White-glove onboarding + support",
					Enterprise: "Dedicated SLA & private Slack"
				}
			},
			{
				name: "Workspace management",
				tiers: {
					Free: false,
					Pro: false,
					Agency: true,
					Enterprise: "Advanced"
				}
			},
			{
				name: "Onboarding + training",
				tiers: {
					Free: false,
					Pro: false,
					Agency: "White-glove onboarding",
					Enterprise: "Custom onboarding, training, playbooks"
				}
			},
			{
				name: "Integrations/API access",
				tiers: {
					Free: false,
					Pro: false,
					Agency: false,
					Enterprise: true
				}
			},
			{
				name: "SSO/SAML support",
				tiers: {
					Free: false,
					Pro: false,
					Agency: false,
					Enterprise: true
				}
			},
			{
				name: "Private Slack channel",
				tiers: {
					Free: false,
					Pro: false,
					Agency: false,
					Enterprise: true
				}
			},
			{
				name: "Custom workflows",
				tiers: {
					Free: false,
					Pro: false,
					Agency: false,
					Enterprise: true
				}
			},
			{
				name: "Billing management dashboard",
				tiers: {
					Free: false,
					Pro: false,
					Agency: true,
					Enterprise: true
				}
			}
		],
		tiers = [
			{
				name: "Free",
				monthlyPrice: 0,
				yearlyPrice: 0,
				description: "For individuals exploring what FLORA can do. Get access to the core creative tools with limited AI credits—enough to experience the power of the canvas.",
				features: [
					"1 seat",
					"20 AI credits per month",
					"Up to 3 projects",
					"Access to standard AI models (text, image, video)",
					"Core canvas tools and workflows"
				],
				cta: {
					label: "Get started",
					href: "/signup?plan=free"
				}
			},
			{
				name: "Pro",
				monthlyPrice: 39,
				yearlyPrice: 29, // 25% savings
				description: "For freelancers and individual creatives who want more power, bigger projects, and faster results—all with direct canvas export and personal workspaces.",
				features: [
					"1 seat",
					"200 AI credits per month",
					"Unlimited personal projects",
					"Faster AI responses (priority processing)",
					"Export options (image, video, layered files)",
					"Custom style training (1 active at a time)",
					"Personal workspace with version history",
					"Email support with fast turnaround"
				],
				cta: {
					label: "Get started",
					href: "/signup?plan=pro"
				},
				highlight: true
			},
			{
				name: "Agency",
				monthlyPrice: 119,
				yearlyPrice: 99, // 20% savings
				description: "For creative teams and design studios that need shared workspaces, reusable components, and collaborative tools to keep output high and reviews smooth.",
				features: [
					"Up to 10 seats",
					"2,500 AI credits per month",
					"Unlimited projects across team workspaces",
					"Shared assets and libraries",
					"Feedback and review tools built into each canvas",
					"Multiple custom styles per workspace",
					"Frictionless team billing and unified dashboard",
					"White-glove onboarding and support",
					"Canvas export history and scheduled exports (by interval)"
				],
				cta: {
					label: "Contact sales",
					href: "/contact?plan=agency"
				}
			},
			{
				name: "Enterprise",
				monthlyPrice: null,
				yearlyPrice: null,
				description: "For large creative orgs that need enterprise-grade support, advanced customization, and automation at scale. Everything in Agency—plus engineering, security, and collaboration tools at the highest level.",
				features: [
					"Flexible seats and usage caps",
					"Custom AI credit tiers",
					"Advanced workspace management and security",
					"SSO/SAML & access controls",
					"SLA-backed premium support",
					"Direct API access and custom integrations",
					"Private Slack channel with FLORA team",
					"Custom onboarding, training, and playbook walkthroughs",
					"2+ custom style libraries across workspaces",
					"Bespoke workflows engineered for your org",
					"Digital procurement and SOC-ready documentation"
				],
				cta: {
					label: "Contact sales",
					href: "/contact?plan=enterprise"
				}
			}
		]
	}: {
		title?: string;
		subtitle?: string;
		tiers?: PricingTier[];
		features?: PricingFeature[];
		tierNames?: string[];
		caption?: string;
	} = $props();

	// State
	let annual = $state(true);
</script>

<section class="section-py section-px container mx-auto">
	<div class="flex flex-col items-baseline justify-between lg:flex-row">
		<SectionHeader {title} {subtitle} />

		<div class="mb-8 flex justify-center">
			<div class="inline-flex items-center rounded-full bg-gray-100 p-0.5 dark:bg-gray-800">
				<Button
					variant="ghost"
					size="sm"
					class=" {!annual ? 'bg-white shadow-sm dark:bg-gray-700' : ''}"
					onclick={() => (annual = false)}
				>
					Monthly
				</Button>
				<Button
					variant="ghost"
					size="sm"
					rounded
					class={annual ? "bg-white shadow-sm dark:bg-gray-700" : ""}
					onclick={() => (annual = true)}
				>
					Annual <span class="text-primary-600 dark:text-primary-400 text-footnote">Save 20%</span>
				</Button>
			</div>
		</div>
	</div>

	<div class="bb grid gap-6 md:grid-cols-2 lg:grid-cols-3">
		{#each tiers as tier}
			<div
				class="flex flex-col rounded-xl bg-white p-6 ring ring-gray-200 transition-all duration-300 dark:bg-gray-800 dark:ring-gray-700"
				class:ring-2={tier.highlight}
				class:ring-primary={tier.highlight}
				class:dark:ring-primary-700={tier.highlight}
				class:translate-y-[-4px]={tier.highlight}
			>
				<div class="mb-8">
					<h3 class="text-title3 mb-4 dark:text-white">{tier.name}</h3>
					<div class="mt-2 flex items-baseline">
						{#if tier.monthlyPrice === null && tier.yearlyPrice === null}
							<span class="text-title2 dark:text-white">Custom</span>
						{:else}
							<NumberFlow
								class="text-title2 [&::part\(suffix\)]:text-caption dark:text-white"
								format={{
									style: "currency",
									currency: "USD",
									trailingZeroDisplay: "stripIfInteger"
								}}
								value={annual ? tier.yearlyPrice : tier.monthlyPrice}
								suffix="/month"
							/>
						{/if}
					</div>
					<p class="text-callout text-emphasis-medium mt-3 dark:text-gray-300">
						{tier.description}
					</p>
				</div>

				<div class="mb-8 flex-grow">
					<ul class="space-y-3">
						{#each tier.features as feature}
							<li class="flex items-center gap-2">
								<IconCheck class="text-primary-600 dark:text-primary-400 size-5 flex-shrink-0" />
								<span class="text-body text-emphasis-medium dark:text-gray-300">{feature}</span>
							</li>
						{/each}
					</ul>
				</div>

				<div class="mt-auto">
					<Button
						href={tier.cta.href}
						variant={tier.highlight ? "primary" : "secondary"}
						class="w-full"
					>
						{tier.cta.label}
					</Button>
				</div>
			</div>
		{/each}
	</div>
	<div class="mt-32">
		<!-- Responsive table wrapper with horizontal scroll on mobile -->
		<!-- <div class=" hidden overflow-x-auto px-4 sm:mx-0 sm:block sm:px-0">
			<table
				class="w-full min-w-full border-separate border-spacing-0 border-gray-200 text-left dark:border-gray-700"
			>
				<thead>
					<tr>
						<th
							class="sticky left-0 min-w-[120px] border-b border-gray-200 bg-white dark:border-gray-700 dark:bg-gray-900"
						>
							<span class="sr-only">Feature</span>
						</th>
						{#each tierNames as tierName}
							<th
								class="text-headline min-w-[100px] border-b border-gray-200 p-4 text-start font-normal dark:border-gray-700"
							>
								{tierName}
							</th>
						{/each}
					</tr>
				</thead>
				<tbody>
					{#each features as feature}
						<tr>
							<td class="text-caption">
								{feature.name}
							</td>
							{#each tierNames as tierName}
								<td
									class="min-w-[100px] border-b border-gray-200 p-4 text-start text-gray-600 dark:border-gray-700 dark:text-gray-300"
								>
									{#if typeof feature.tiers[tierName] === "boolean"}
										{#if feature.tiers[tierName]}
											<IconCheck
												class="text-primary-600 dark:text-primary-400 mx-auto size-5 sm:mx-0"
											/>
										{:else}
											<IconX class="mx-auto size-5 text-gray-400 sm:mx-0" />
										{/if}
									{:else}
										{feature.tiers[tierName]}
									{/if}
								</td>
							{/each}
						</tr>
					{/each}
				</tbody>
			</table>
		</div> -->

		<!-- Mobile feature comparison (alternative view for very small screens) -->
		<div>
			<!-- Universal pricing comparison for mobile -->
			<div class="overflow-x-auto">
				<table class="w-full border-collapse">
					<!-- Sticky header with tier names -->
					<thead class="border-border sticky top-0 z-10 border-b">
						<tr>
							<th class="min-w-[120px] py-3 text-left">
								<span class="sr-only">Feature</span>
							</th>
							{#each tierNames as tierName, i}
								<th class="text-caption min-w-[100px] py-3 text-left dark:text-white">
									{tierName}
								</th>
							{/each}
						</tr>
					</thead>
					<tbody class="divide-border divide-y">
						{#each features as feature}
							<tr>
								<td class="text-body py-3 pr-8 font-medium lg:pr-0 dark:text-white">
									{feature.name}
								</td>
								{#each tierNames as tierName, i}
									<td class="py-3">
										{#if typeof feature.tiers[tierName] === "boolean"}
											{#if feature.tiers[tierName]}
												<IconCheck class="text-primary-900 dark:text-primary-400 size-5" />
											{:else}
												<IconX class="size-5 text-gray-400" />
											{/if}
										{:else}
											<span class="text-callout font-medium text-gray-700 dark:text-gray-300">
												{feature.tiers[tierName]}
											</span>
										{/if}
									</td>
								{/each}
							</tr>
						{/each}
					</tbody>
				</table>
			</div>
		</div>
	</div>
	<LogoScroller />
</section>

<style lang="postcss">
	@reference '../../../app.css';

	:global(number-flow-svelte)::part(suffix) {
		@apply text-sm text-gray-400 dark:text-gray-500;
	}
</style>
