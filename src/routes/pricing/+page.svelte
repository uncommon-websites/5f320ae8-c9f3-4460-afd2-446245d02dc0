<script lang="ts">
	// Types
	import type { PageProps } from "./$types";

	// Components
	import Features from "$lib/components/layout/Features.svelte";
	import Testimonials from "$lib/components/layout/Testimonials.svelte";
	import CallToAction from "$lib/components/layout/CallToAction.svelte";
	import Pricing from "$lib/components/layout/Pricing.svelte";

	// Props
	const { data }: PageProps = $props();
</script>

<Pricing />

<Testimonials
	testimonials={[
		{
			name: "Emre Kaya",
			position: "Creative Director",
			company: "Studio Hex",
			quote:
				"We’re saving hours per project. FLORA lets us concept, refine, and present winning ideas faster—and our clients feel the impact.",
			image:
				"/generated/image-a-professional-headshot-of-a-turkish-mal.webp"
		},
		{
			name: "Brielle Carter",
			position: "Art Supervisor",
			company: "FrameForge",
			quote:
				"FLORA brought a real rhythm to our brand workflow. We spend less time on piecing steps together, and more time delighting clients.",
			image:
				"/generated/image-a-professional-headshot-of-a-black-femal.webp"
		},
		{
			name: "Riley Zhou",
			position: "Innovation Lead",
			company: "Ember Arcade",
			quote:
				"We can now link text, image, and motion models into one path and preview ideas quickly. It’s unlocked a new pace of ambition on each game concept.",
			image:
				"/generated/image-a-professional-headshot-of-an-east-asian.webp"
		}
	]}
/>

<CallToAction
  title="Bring ideas to life—faster, together"
  subtitle="FLORA gives your creative team AI-powered tools to build, iterate, and collaborate—without losing control of the process."
  description="Moodboard, concept, and prototype in a single infinite canvas that adapts to you. Get started free and experience workflow freedom, team collaboration, and support."
  imageSrc="/generated/image-a-joyful-and-imaginative-professional-wo.webp"
  callsToAction={[
    {
      href: '/signup',
      label: 'Start free',
      variant: 'primary'
    },
    {
      href: '/contact',
      label: 'Talk to sales',
      variant: 'secondary'
    }
  ]}
/>
