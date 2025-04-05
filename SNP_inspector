from pysanger_SNPplot import *
import cv2
import matplotlib.pyplot as plt

def snp_inspector(data_file, target_template, locus_start, locus_end, strand=1):
    # Read ABI file names from a text file
    with open(data_file, "r") as file:
        abi_filenames = [line.strip() for line in file]

    # Initialize an empty list to store the ABI file paths
    abi_filepaths = []

    # Loop through each ABI filename
    for abi_filename in abi_filenames:
        # Append ".ab1" extension and store in the list
        abi_filepath = f"{abi_filename}.ab1"
        abi_filepaths.append(abi_filepath)

    # Loop through each ABI file using the list
    for abi_filepath in abi_filepaths:
        # Load ABI data
        abidata = abi_to_dict(abi_filepath)

        # Generate consensus sequences
        fseq, rseq = generate_consensusseq(abidata)

        # Visualize and create a figure
        fig = visualize(abidata, template=target_template, region="aligned", strand=1)

        # Remove file extension and set it as title
        filename_without_extension = abi_filepath.rsplit(".", 1)[0]
        fig.suptitle(f"ID: {filename_without_extension}", fontsize=10, y=1.01, x=0.1)

        # Add highlight for locus
        locus = [locus_start, locus_end]
        for ax in fig.get_axes():
            for x in locus:
                ax.axvline(x, color="darkorange")

        # Save the figure
        fig.savefig(f"{filename_without_extension}.png", bbox_inches="tight")

        plt.close(fig)

if __name__ == "__main__":
    # Example of how to use the module
    data = "ab1_file_list.txt"
    target = "AATTTAGTC"
    snp_inspector(data_file, target_template, locus_start, locus_end, strand=1)
